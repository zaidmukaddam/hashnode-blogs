## Wassword: A wonderful password generator built in Flutter

Hi, in this post I want to show you one of the most loved side projects that a long time ago introduce me to Flutter. In these years I made lots of changes and experiments with this project and I want to share with you the final result to date.

Wassword is a password generator and as said in its description:


> "With Wassword you can easily generate complex passwords and use them for your online accounts. Choose length and chars to be used and generate your passwords safely. Everything works offline and nothing is shared, your safety comes first."

so with Wassword you can create passwords with **Numbers**, **Lower case letters**, **Upper case letters**, and **Symbols**from **8 to 32 chars**. Once you created your password you can copy it and use with your account, share it and there's no limit on how many password you can create. 

These are some screenshots that show its functionality:

![app.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1636222354175/bEcLdoqxl.jpeg)

Wassword is Open Source with  [MIT License](https://opensource.org/licenses/MIT)  and you can find the repo on GitHub with all the source code:  [wassword-flutter](https://github.com/zaidmukaddam/wassword-flutter).

# Project Structure

Let's dive a little into the project structure to explain how I organize all the code and what packages I used. To start these are my dependencies:

```yaml
dependencies:
  ...
  bloc: ^7.2.1
  equatable: ^2.0.3
  flutter_bloc: ^7.3.1
  fluttertoast: ^8.0.8
  google_fonts: ^2.1.0
  share_plus: ^2.2.0
  url_launcher: ^6.0.10

dev_dependencies:
  ...
  flutter_launcher_icons: ^0.9.2
  flutter_native_splash: ^1.2.3
``` 

I use the  [bloc package](https://bloclibrary.dev/#/)  to manage the state of the app and I choose to go with one  [Cubit](https://bloclibrary.dev/#/coreconcepts?id=cubit) for its simplicity because my state is the password that I want to show and all the password characteristics like number of chars, numbers and so on.  

The other packages are pretty standard:  [customize the font](https://pub.dev/packages/google_fonts) ,  [share generated password](https://pub.dev/packages/share_plus) ,  [open links](https://pub.dev/packages/url_launcher) ,  [create app icon](https://pub.dev/packages/flutter_launcher_icons)  and [create splash screen](https://pub.dev/packages/flutter_native_splash) .

This is the structure that I used to manage the code in the **lib** folder and keep the same stuff in the same place:

- **cubit**: in this folder, I put the cubit and the cubit state that lets me manage password characteristics. To change the state I create one method for every characteristic that I want to change, so: `changeLowercase`, `changeUppercase` and so on;
- **pages**: folder where I put the code for the two pages of the application, both stateless widget, one for the main page with the password creation and one for the about page where I put some information about myself and my social account;
- **styles**: folder where I create variables to theme the app and to make the design consistent;
- **ui**: folder where I put some reusable UI components across the app like buttons and rows;
- **utils**: in this folder, there's the function that generates the password based on the selected options.

# Takeaways

There are many takeaways from this app but two of them that I want to recall are related to the password generator and the slider to set the number of chars in the password.

To generate the password I used the generatePassword method inside `password_generator.dart` file in `lib/utils`

```dart
/*
 * @desc Function to generate passwords based on some criteria
 * @param bool isWithLetters: password must contain letters
 * @param bool isWithUppercase: password must contain uppercase letters
 * @param bool isWithNumbers: password must contain numbers
 * @param bool isWithSpecial: password must contain special chars
 * @param int _numberCharPassword: password length
 * @return string: new password
 */
String generatePassword(
    {required bool isWithLowercase,
    required bool isWithUppercase,
    required bool isWithNumbers,
    required bool isWithSpecial,
    required int numberCharPassword}) {
  String _lowerCaseLetters = "abcdefghijklmnopqrstuvwxyz";
  String _upperCaseLetters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  String _numbers = "0123456789";
  String _special = "@#=+!£\$%&?[](){}-_";

  String _allowedChars = "";

  _allowedChars += (isWithLowercase ? _lowerCaseLetters : '');
  _allowedChars += (isWithUppercase ? _upperCaseLetters : '');
  _allowedChars += (isWithNumbers ? _numbers : '');
  _allowedChars += (isWithSpecial ? _special : '');

  if (_allowedChars.length == 0) {
    return '';
  }

  //If I can create a password because I've got some char to use
  int i = 0;
  String _result = "";
  while (i < numberCharPassword) {
    int randomInt = Random.secure().nextInt(_allowedChars.length);
    _result += _allowedChars[randomInt];
    i++;
  }

  return _result;
}
``` 

To style the Slider I use this wonderful article on Medium:  [Flutter: Sliders DeMystified](https://medium.com/flutter-community/flutter-sliders-demystified-4b3ea65879c)  where I use a combination of  [SliderTheme](https://api.flutter.dev/flutter/material/SliderTheme-class.html)  and  [SliderComponentShape](https://api.flutter.dev/flutter/material/SliderComponentShape-class.html)  to integrate the slider inside the app's theme. You can find all the code in the `pages/home_page.dart` and `ui/custom_slider_thumb_circle.dart`.

# Download and Use

You can download Wassword from the Github Releases:  [Wassword](https://github.com/zaidmukaddam/wassword-flutter/releases) - Wonderful Password Generator. It has got all the functionalities of the Android version while the other iOS and Web Versions aren't available as of now.

Hope you learned something new today!

Don't hesitate to comment below to raise any queries or suggestions.

Will see you guys very very soon!! :)