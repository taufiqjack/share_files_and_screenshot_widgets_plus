# share_files_and_screenshot_widgets_plus

## Important

This is the author's library https://pub.dev/packages/share_files_and_screenshot_widgets

I just upgraded it to null safety

This pub lets you share any kind of files (csv, mp4, png etc), take screenshot of the widgets you want and return as Image and share them directly as well in the form of an image.

## Usage

## Example

To use this package :

* add the dependency to your [pubspec.yaml] file.

```yaml
  dependencies:
    flutter:
      sdk: flutter
    share_files_and_screenshot_widgets_plus: ^1.0.3
```

### How to use

#### Take ScreenShot of Widgets

```dart
//define
GlobalKey previewContainer = GlobalKey();

//wrap your widget with
RepaintBoundary(
  key: previewContainer,
  child: YourWidget()
),

//call this function for taking screenshot
ShareFilesAndScreenshotWidgets()
    .takeScreenshot(previewContainer, originalSize)
    .then((Image value) {
  setState(() {
    _image = value;
  });
});
```

#### Directly Share ScreenShot of Widgets

```dart
//define
GlobalKey previewContainer = new GlobalKey();

//wrap your widget with
RepaintBoundary(
  key: previewContainer,
  child: YourWidget()
),

//call this function for sharing screenshot
ShareFilesAndScreenshotWidgets().shareScreenshot(
  previewContainer,
  originalSize,
  "Title",
  "Name.png",
  "image/png",
  text: "This is the caption!");
```

#### Share Any Type of File

```dart
ByteData bytes =
    await rootBundle.load('assets/example.jpg');
Uint8List list = bytes.buffer.asUint8List();
ShareFilesAndScreenshotWidgets().shareFile(
    "Title", "Name.jpg", list, "image/jpg",
    text: "This is the caption!");
```
```dart
ByteData bytes =
    await rootBundle.load('assets/example.mp4');
Uint8List list = bytes.buffer.asUint8List();
ShareFilesAndScreenshotWidgets().shareFile(
    "Title", "Name.mp4", list, "video/mp4",
    text: "This is the caption!");
```
```dart
ByteData bytes =
    await rootBundle.load('assets/example.mp3');
Uint8List list = bytes.buffer.asUint8List();
ShareFilesAndScreenshotWidgets().shareFile(
    "Title", "Name.mp3", list, "audio/mp3",
    text: "This is the caption!");
```


## * iOS, option save file in dialog share.
Your project need create with swift.
Add the following keys to your Info.plist file, located in <project root>/ios/Runner/Info.plist:
 * NSPhotoLibraryAddUsageDescription - describe why your app needs permission for the photo library. This is called Privacy - Photo Library Additions Usage Description in the visual editor
# License

    Copyright 2020 Jay Mehta

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.