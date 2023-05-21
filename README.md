# dgtchess

A JavaScript connector for the electronic [DGT](http://dgtprojects.com) chess board, working in the browser with WebSerial.

## Browser Usage

The client version relies on the browser's [Web Serial API](https://wicg.github.io/serial/), which is [currently supported](https://caniuse.com/web-serial) only by Google Chrome, Microsoft Edge and Opera

The `Board` constructor expects an open port as returned by the Web Serial API as its first argument.

In `example/index.html`, we provide a standalone example web page that loads the DGT chess board's information and dynamically displays the current position:

![Screencast](example/screencast.gif)

## Changes

Changes from the [original code](https://github.com/fnogatz/dgtchess)
* changed WebSerial initialisation so that it works (for me)
* added in correct vendor/device IDs for the DGT Smart Board
```
{ usbVendorId: 0x045b, usbProductId: 0x8111 }
```
* removed node.js support
* changed code to not use modules etc - now it works from file:// so easier to prototype with
* added a quick hack to avoid a crash here in Board.js - not sure currently why that's happening
```
message.set(value, pos)
```

## Background

The protocol for communicating with the electronic chess boards is well documented by DGT in [their developer section](http://www.dgtprojects.com/site/index.php/dgtsupport/developer-info). There you can find the [DGT Electronic Board Protocol Description (version 20120309)](http://www.dgtprojects.com/site/index.php/dgtsupport/developer-info/downloads/doc_download/85-dgt-electronic-board-protocol-description-version-20120309) which is the base for this JavaScript implementation.
