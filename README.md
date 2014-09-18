cordova-plugin-datagram
=======================

Cordova plugin for sending datagram/UDP. Supports multicast UDP.


example

```js
var datagram = cordova.require("in.girish.datagram.datagram");
var socket = datagram.createSocket("udp4");
var myPort = 3000;
var targetPort = 3001;
var targetIp = "target device ip";

socket.bind(listenPort, function(data) {
  alert("bind \n" + JSON.parse(data));
});

socket.on("message", function(data, info) {
  console.log(data + " / " + JSON.stringify(info));
});

var button = document.getElementById("button");
button.addEventListener(button, "click", function() {
  var message = "HelloWorld";
  if (message.length > 20480) {
    alert("Too large!");
    return;
  }
  socket.send(message, targetIp, targetPort, function() {
    alert("done");
  });
});
```
