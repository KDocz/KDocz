**How do I include a testng.xml file in the root of the tests.jar file for
Device Farm?**

Issue

To apply the testng.xml file to the Appium TestNG test package for AWS Device
Farm, I need to add the testng.xml file to the root of the \*-tests.jar file.
How do I do that?

Short Description

With the introduction of Custom Test Environment, TestNG XML will be the used to
run the tests inside the project test code. For that purpose, this XML has to be
present inside the Testing Jar which is created as part of the test code
compilation.

Users can configure their test code to package this XML into the Testing Jar as
part of the maven build.

**Note**: In Device Farm's [standard
environment](https://docs.aws.amazon.com/devicefarm/latest/developerguide/test-environments.html#test-environments-standard) only
a subset of features are supported for the testng.xml file. If priority, the
include tag, the exclude tag, complex grouping, or using parameters from the
testng.xml file are required for the project, then use the [custom
environments](https://docs.aws.amazon.com/devicefarm/latest/developerguide/test-environments.html#custom-test-environment).

Resolution

To achieve this, following things are required to be taken care of: -

1.  User has to make sure to place his test code inside the root test folder
    i.e. –

    SP4 - *\<project_root\>/testresources/TestNG/*

    Before SP4 - *\<project_root\>/test/TestNG/*

    **Note** – User should make sure his/her pom.xml resides under this
    directory.

2.  User has to write a TestNG XML as per user preference and place it at the
    following location

    *\<root_test_folder\>/src/test/resources*

    ![](media/e4f5dce2487d7230281fd67c66d7a31b.tiff)

3.  After the files are in place, user has to include *testresources* tags in
    the pom.xml to explicitly reference the directory:

\<testResources\>

\<testResource\>

\<directory\>\${project.basedir}/\<root_test_folder\>/src/test/resources\</directory\>

\</testResource\>

\</testResources\>

1.  Next step is to modify the pom.xml to include the surefire plugin to
    reference the TestNG XML file for local executions:

\<plugin\>

\<groupId\>org.apache.maven.plugins\</groupId\>

\<artifactId\>maven-surefire-plugin\</artifactId\>

\<version\>2.12.4\</version\>

\<configuration\>

\<suiteXmlFiles\>
\<suiteXmlFile\>src/test/resources/testng.xml\</suiteXmlFile\>\</suiteXmlFiles\>

\</configuration\>

\</plugin\>

Please note, for more than one TestNG XML multiple \< suiteXmlFile \> tags have
to be used.

1.  To check on local, user can build the test code to create a dependencies zip
    which contains the Testing JAR. Zip with the dependencies will be present
    inside *\<root_test_folder\>/target* directory.

    Package the tests using maven *clean* and *package* commands at the test
    root folder. The -DskipTests=true option specifies that the build shouldn’t
    run the unit tests.

mvn clean package -DskipTests=true

1.  Extract the zip, use *xf* command to extract the jar to verify that TestNG
    XML file is present at the desired location (root, by default):

jar xf nameOfTheProjectFromPom-1.0-SNAPSHOT-tests.jar

Alternatively, the *unzip* command can also extract the contents of the jar:

unzip nameOfTheProjectFromPom-1.0-SNAPSHOT-tests.jar -d sampletestsjarcontents

If the XML is in place, the target folder has to be removed and the code has to
be checked-in into a branch in Git. Now, the user can run his/her tests on
AppFactory in the Custom Test Environment.

Please note, that steps 3 and 4 are only for verification and tests will be
compiled by AppFactory during runtime unless the zip with dependencies is
directly provided via build parameters.  
For more information on this, please visit [AWS
Documentation](https://aws.amazon.com/premiumsupport/knowledge-center/xml-file-tests-jar-file-device-farm/).
