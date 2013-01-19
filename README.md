Spacebrew Javascript Wildstyle Examples
---------------------------------------

This repo contains the `wildstyle` Javascript examples for Spacebrew. We call these examples `wildstyle` because we don't actively maintain them. They were created out of explorations and prototypes developed at the LAB; they are also more advanced and less consistently-structured than the core examples included with the library.

Current Version: 1.0.0
Latest Update: January 16, 2013

Jump to:
* [Using the Spacebrew Javascript Library](#using-javascript-library)
* [Spacebrew Wildstyle Examples](#javascript-wildstyle-examples)
  
About Spacebrew
===============
Spacebrew is an open, dynamically re-routable software toolkit for choreographing interactive spaces. Or, in other words, a simple way to connect interactive things to one another. Every element you hook up to the system can subscribe to, and publish data feeds. Each data feed has a data type. There are three different data types supported by Spacebrew: boolean (true/false), number range (0-1023) or string (text). Once elements are set up, you can use a web based visual switchboard to connect or disconnect publishers and subscribers to each other. 

[Learn more about Spacebrew here.](http://docs.spacebrew.cc/)

Using Javascript Library
========================  
  
Before you get started you need to download the spacebrew library, and add it to your project's directory so that you can import it into your web app's code. To download the latest version of the library just click the "ZIP" button above.  

###1. Import javascript library into your project  
Import the javascript library into your project using a script tag in the appropriate html page. We usually include the page's javascript code in a separate file as well. This file should be imported after the library.  
  
```
<script src="path/sb.js"></script>
<script src="path/your_scripts.js"></script>
```
  
###2. Create a Spacebrew object  
In `your_scripts.js` file, the first thing you need to do is create new instance of a Spacebrew Client object using the `Spacebrew.Client` constructor and assign it to a variable or object attribute.  
  
```
var sb = new Spacebrew.Client( server, name, description );
```
  
**Constructor Parameters**
The constructor parameters, `server`, `name`, and `description`, are all optional. When running in a browser, the Spacebrew Client library will look for the server, app name, and app description in the query string; using `server`, `name`, and `description` as keys.  
  
If server is not specified in the query string or constructor, then the app will attempt to connect to a Spacebrew server hosted locally. The name will default to the app's full URL, if no name is provided via the query string or constructor. The description will remain blank if no description is specified. If you want to connect to the cloud server just point spacebrew to `sandbox.spacebrew.cc`.  

###3. Configure Base Name and Description Feeds  
You can also set the base app name and description using the `Spacebrew.Client` library's `name()` and `description()` methods. The app's name and description must be set before the Spacebrew connection is established.
  
```
sb.name("myApp")
sb.description("this is a spacebrew app.")
```
      
###4. Configure Data Subscription and Publication Feeds  
The next step is adding the subscription and publication data feeds. Each one needs to be labelled and assigned an appropriate data type - `"string"`, `"range"`, of `"boolean"`. You can also optionally define a default value for any publication feed. 

```
sb.addPublish( name, type, default );
sb.addSubscribe( name, type );
```
  
###5. Define lifecycle and message event handler methods
Spacebrew offers lifecycle event hooks for connection open and close events - `onOpen`, and `onClose`; and for incoming message events of each data type - `onStringMessage`, `onRangeMessage`, of `onBooleanMessage`. You need to define the message handler methods in order to capture data from your subcriptions data feeds.
  
```
sb.onStringMessage = function onString( name, value );
sb.onRangeMessage = function onRange( name, value );
sb.onBooleanMessage = function onBoolean( name, value );
sb.onOpen = function onOpen();
sb.onClose = function onClose();
```
  
###6. Connect to Spacebrew
Now that you have configured the Spacebrew object it is time to connect to the Spacebrew server. 
  
```
sb.connect();
```
  
###7. Send messages
The `send` method enables you to publish messages via one of the publication data feeds. It accepts three mandatory parameters, a channel name, a data type, and a value. The value needs to correspond to the data type, otherwise the message will be ignored by the server.
  
```
sb.send( name, type, value )
```
  
Javascript Wildstyle Examples
===========================

Here is a list of the wildstyle examples that are included in this repo. 

###Phone Events
Web app tha forwards phone motion events (accelerometer and gyrometer data) to Spacebrew. It also accepts range messages from Spacebrew to set hue, saturation, and lightness values of the app's background color.
  
###Slideshow

  
###Speech

  
###Text Transform


###URL Launcher


  
License  
=======  
  
The MIT License (MIT)  
Copyright © 2012 LAB at Rockwell Group, http://www.rockwellgroup.com/lab  
  
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:  
  
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.  
  
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.  

