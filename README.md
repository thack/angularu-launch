# AngularU Launch

### Obectives

* Create native UX using HTML5 technology.
* Demonstrate how Cordova is more capable than web applications.

### Step 1

* Install Ionic and Cordova
    * ``npm install -g ionic cordova``

### Step 2

* Create new project
    * ``ionic start launch blank``
    * ``cd launch``
    * ``ionic platform add ios`` (Should be automatic on OSX)
    * ``ionic platform add android``

### Step 3

* Run on emulator or device
    * iOS recommended:
        * ``ionic emulate ios -l -c``
        * Live reload and console output.
    * Android recommended (Device or Genymotion):
        * ``ionic run android -l -c``
        * Live reload and console output.
    * ``ionic run ios``
        * Can be tricky because of certificate security
    * ``ionic emulate android``
        * Slow without HAXM. HAXM is buggy on Mac.

### Step 4

* Add www/video folder and add moments.mp4 video file.
* Remove everything within the body tag.
* Add video to body tag to index.html:
```
  <body ng-app="starter">
    <video id="video" src="video/moments.mp4" width="445" autoplay loop webkit-playsinline></video>
  </body>
```

### Step 5

* Add AllowInlineMediaPlayback to config.xml:
```
  <preference name="AllowInlineMediaPlayback" value="true"/>
```

### Step 6

* Add img to the body tag within index.html.
* Add text overlay after video.
* Add button bar after overlay.
```
  <body ng-app="starter">
    <img id="logo" src="img/ionic.png">
    <video id="video" src="video/moments.mp4" width="445" autoplay loop webkit-playsinline></video>
    <div id="overlay">
      <h1>Welcome</h1>
      Let's Get Started!
    </div>
    <div id="buttons" class="button-bar">
      <button class="button button-dark">LOG IN</a>
      <button class="button button-balanced">SIGN UP</a>
    </div>
  </body>
```

* Add CSS:
```
  #logo {
      position: absolute;
      top: 50px;
      left: 123.5px;
      text-align: center;
      font-size: 20px;
      width: 128px;
      z-index: 2147483647;
  }
  #overlay {
      position: absolute;
      bottom: 100px;
      color: #FFF;
      text-align: center;
      font-size: 14px;
      background-color: rgba(221, 221, 221, 0.3);
      width: 375px;
      padding: 10px 0;
      z-index: 2147483647;
  }
  #overlay > h1 {
      color: #FFF;
      font-size: 16px;
      font-weight: bold;
  }
  #video {
      position: absolute;
      top: 0;
      left: -35px;
      z-index: 1;
  }
  #buttons {
      position: absolute;
      bottom: 0;
      z-index: 2147483647;
  }
  #buttons > button {
      font-weight: 500;
  }
```

### Step 7

* Add Crosswalk
    * ``ionic browser add crosswalk``
* Run again on Android:
    * ``ionic run android``

### Step 8

* Add Status Bar plugin:
    * ``ionic plugin add cordova-plugin-statusbar``

* Remove status bar code from app.js:
```
  if(window.StatusBar) {
    StatusBar.styleDefault();
  }
```

### Extra Credit

* On application resume, video needs to be restarted.
