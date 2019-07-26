## Flutter Icon Font Generator

![Pub](https://img.shields.io/pub/v/icon_font_generator)

Convert all *.svg icons from dir to icon-font (.ttf) and generates flutter compatible dart class. 

Abstraction layer for NodeJs package `icon-font-generator`

## Requirements
Node.JS v11+

## Install:

```
$ pub global activate icon_font_generator
```

## Params:
- `--from` - Input dir with svg's
- `--out-font` - Output icon font path (to file, for example: lib/font.ttf)
- `--out-flutter` - Output flutter icon class (to file, for example: lib/icons.dart)
- `--class-name` - The class name is also the font name used in pubspec.yaml (as font name)
- `--height` - Fixed font height value, defaults: 512
- `--ascent` - Offset applied to the baseline, defaults: 240
- `--package` - Name of package for generated icon data
- `--indent` - Indent for generating dart file, for example: '   ', default: '  '
- `--mono` - Make font monospace, default: true

## Example
File structire:
```
project
└───icons
│   │   account.svg
│   │   arrow_left.svg
│   │   arrow_right.svg
│   │   collection.svg
│   
└───lib
│   │   icon_font
│   │   widgets
```
Run command:
```
$ icon_font_generator --from=icons --class-name=UiIcons --package=project --out-font=lib/src/icon_font/ui_icons.ttf --out-flutter=lib/src/widgets/icons.dart
```
Generated to:
```
project
└───icons
│   │   account.svg
│   │   arrow_left.svg
│   │   arrow_right.svg
│   │   collection.svg
│   
└───lib
│   └───widgets
│   |   │   icons.dart
│   │
│   └───icon_font
│       │   ui_icons.ttf
```
Generated icons.dart:
```dart
import 'package:flutter/widgets.dart';

@immutable
class UiIconsData extends IconData {
  const UiIconsData(int codePoint)
      : super(
          codePoint,
          fontFamily: 'UiIcons',
        );
}

@immutable
class UiIcons {
  UiIcons._();

  // Generated code: do not hand-edit.
  static const IconData account = UiIconsData(0xe000);

  static const IconData arrowLeft = UiIconsData(0xe001);

  static const IconData arrowRight = UiIconsData(0xe002);

  static const IconData collection = UiIconsData(0xe003);
}
```
And also need add font to pubspec.yaml:
```yaml
...

flutter:
  fonts:
    - family: UiIcons
      fonts:
        - asset: lib/src/icon_font/ui_icons.ttf
```