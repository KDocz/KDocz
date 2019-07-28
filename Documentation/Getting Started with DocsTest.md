---
title: Getting Started with DocsTest
---

This is where you show your users how to set it up. You can use code samples,
like this: [block:api-header] { "title": "Segment Widget" } [/block] The
SegmentedUI widget is a container that contains data of a certain type. A
Segment helps you to display a certain type of information at one place, which
makes it easier for users to view the requisite information.

You can use the Segment widget to get data from services, group services
together, use templates to create the layout of each row, perform actions when
users click a record, implement animations for each row, and much more. These
features have been explained in detail here:

**Data Handling**: Retrieve data from various services and display it in your
application by using Segment widgets. For example, if you have a service that
contains the data of all the employees in an organization, you can retrieve this
information and display it in your application by using a Segment widget.

**Group Data**: Group data into different sections by using Segment widgets. For
example, after you have retrieved all employees’ data from the service mentioned
earlier, you can categorize employees based on their respective departments by
using another Segment widget.

**Define Templates**: Create templates to define reusable data for Segment
widgets. Templates help you to attain a consistent look-and-feel for the rows
and sections of a Segment widget.

**Animations**: Add animation effect to the rows of a Segment widget in order to
perform a specific task. One of the main uses of this capability is to enable
the option that allows users to delete a Segment row, by swiping the row from
right to left.

**Row Click events**: Assign a variety of actions to Segment widgets, which are
performed when users click a Segment record. For example, if you have a Segment
that contains the list of all employees in an organization, you can click any
row to move to another form where the details of the specific employee are
displayed.

Widgets are normally added to your Kony application using Kony Visualizer, but
can also be added from code. For general information on using widgets in
Visualizer, see Designing an Application in the Kony Visualizer User Guide.

For general information on the SegmentedUI widget, refer the Segment2 topic in
the Kony Visualizer User Guide.

Segment Widget – Introduction
-----------------------------

[block:embed] { "html": "", "url":
"https://www.youtube.com/watch?v=0I4lu_Gvp4M&feature=youtu.be", "title":
"Segment Widget - Introduction", "favicon":
"https://s.ytimg.com/yts/img/favicon-vfl8qSV2F.ico", "image":
"https://i.ytimg.com/vi/0I4lu_Gvp4M/hqdefault.jpg" } [/block] \#\# Segment
Widget - Advanced

[block:embed] { "html": "", "url":
"https://www.youtube.com/watch?v=eKsHBTKgjs8&feature=youtu.be", "title":
"Segment Widget - Advanced", "favicon":
"https://s.ytimg.com/yts/img/favicon-vfl8qSV2F.ico", "image":
"https://i.ytimg.com/vi/eKsHBTKgjs8/hqdefault.jpg" } [/block] \#\#\# doLayout
Event This event is invoked for every widget when the widget position and
dimensions are computed.

**Syntax** [block:code] { "codes": [ { "code": "doLayout()", "language":
"javascript" } ] } [/block] **Read/Write**

Read + Write

**Remarks**

This event is invoked for all the widgets placed inside flex containers. This
event is invoked in the order in which the widgets are added to the widget
hierarchy and expect the frame property of the widget is calculated and
available for use within this event.

This event is used to set the layout properties of child widgets in the relation
to self and peer widgets whose layout is not yet performed.

When doLayout event is called in a Segment, the platform will add the context
parameter.

The number of times this event invoked may vary per platform. It is not
recommended to write business logic assuming that this function is invoked only
once when there is a change in positional or dimensional properties. This event
will not trigger when transformations are applied though widget is moved or
scaled or rotated from its original location.

[block:code] { "codes": [ { "code": "//doLayout example1 =
createButton("Button1", null, doLayoutButton1);2 = createButton("Button2", null,
doLayoutButton2);3 = createButton("Button3", null,
doLayoutButton3);doLayoutButton1() {kony.print("Calling doLayoutButton1 " +
button1.frame["height"]);button2.top =
button1.frame["height"];}doLayoutButton2() {kony.print("Calling doLayoutButton2
" + (button2.frame["y"] + button2.frame["height"]));button3.top =
button2.frame["y"] + button2.frame["height"];}widgetCount = 1;createButton(text,
actionCallback, doLayoutCallback) {var button = new kony.ui.Button({"id":
"button" + widgetCount,"isVisible": true,"text": text,"skin": "skin5","onClick":
actionCallback}, {"margin": [0, 0, 0, 0],"widgetAlignment":
constants.WIDGET_ALIGN_CENTER,"contentAlignment":
constants.CONTENT_ALIGN_MIDDLE_LEFT,"containerWeight": 100}, {});if
(doLayoutCallback) {kony.print("do Layout callback:" +
doLayoutCallback);button.doLayout = doLayoutCallback;}widgetCount++;return
button;}", "language": "javascript" } ] } [/block] **Platform Availability**

iOS Android Windows SPA [block:code] { "codes": [ { "code":
"\$http.post('/someUrl', data).success(successCallback);('test');", "language":
"javascript" } ] } [/block] Try dragging a block from the right to see how easy
it is to add more content!
