<img src="https://github.com/C-Dev66/SignInScreen/blob/main/screenshots/Screen%20Shot%202022-05-16%20at%205.23.56%20PM.png" alt="HomePage"/>

# SignInScreen
> This multi-platform application(Andoird, iOS, Web) creates a LoginScreen that contains three text fields: first name, last name, and username. As the user fills out the fields, a progress bar animates along the top of the sign in area. When all three fields are filled in, the progress bar displays in green along the full width of the sign in area, and the Sign up button becomes enabled. Clicking the Sign up button causes a welcome screen to animate.

---

### Table of Contents:

- [Description](#description)
- [Code Snippets](#code-snippets)
- [Summary](#summary)
- [Demo](#demo)




---

## Description

We will create a Flutter Web App with bject-oriented programming, and concepts such as variables, loops, and conditionals.

- Basic structure of a Flutter app
- How to implement a Tween animation
- How to implement a stateful widget
- How to use the debugger to set breakpoints


---

## Code Snippets

> Setting up the application
```
// Check Flutter Instalation

flutter doctor

// Search for Available Devices

flutter devices
```

> Adding user sign-in RSVP
```dart
Consumer<ApplicationState>(
	builder: (context, appState, _) => Authentication(
		email: appState.email,
        loginState: appState.loginState,
        startLoginFlow: appState.startLoginFlow,
        verifyEmail: appState.verifyEmail,
        signInWithEmailAndPassword: appState.signInWithEmailAndPassword,
        cancelRegistration: appState.cancelRegistration,
        registerAccount: appState.registerAccount,
        signOut: appState.signOut,
    ),
),

```

## Observations
- The entire code for this example lives in the lib/main.dart file
- If you know Java, the Dart language should feel very familiar
	- All of the app’s UI is created in Dart code
- The app’s UI adheres Material Design, a visual design language that runs on any device or platform.
- In Flutter, almost everything is a Widget. Even the app itself is a widget. The app’s UI can be described as a widget tree.


> Create WelcomeScreen Widget & SignUpForm
```dart
class WelcomeScreen extends StatelessWidget {
  const WelcomeScreen({Key? key}) : super(key: key);
...

class SignUpForm extends StatefulWidget {
  const SignUpForm();

  @override
  _SignUpFormState createState() => _SignUpFormState();
}

class _SignUpFormState extends State<SignUpForm> {
  final _firstNameTextController = TextEditingController();
  final _lastNameTextController = TextEditingController();
  final _usernameTextController = TextEditingController();

  double _formProgress = 0;

  void _showWelcomeScreen() {
    Navigator.of(context).pushNamed('/welcome')
```

> Enable sign in progress tracking
```dart
      onChanged: _updateFormProgress,
      child: Column(
        mainAxisSize: MainAxisSize.min,
        children: [
          AnimatedProgressIndicator(value: _formProgress),
          Text('Sign up', style: Theme.of(context).textTheme.headline4),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: TextFormField(
              controller: _firstNameTextController,
              decoration: const InputDecoration(hintText: 'First name'),
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: TextFormField(
              controller: _lastNameTextController,
              decoration: const InputDecoration(hintText: 'Last name'),
            ),
          ),
...
```

> Add animations for sign in progress
```dart
class _AnimatedProgressIndicatorState extends State<AnimatedProgressIndicator>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<Color?> _colorAnimation;
  late Animation<double> _curveAnimation;

  @override
  void initState(){
    super.initState();
    _controller = AnimationController(
        duration: const Duration(milliseconds: 1200), vsync: this);

    final colorTween = TweenSequence([
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.red, end: Colors.orange),
        weight: 1,
      ),
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.orange, end: Colors.yellow),
        weight: 1,
      ),
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.yellow, end: Colors.green),
        weight: 1,
...
```

---

## Summary

Creating this application adds another tool into my arsenal. Having a user sign in screen is crucial to most development projects.Structing this in flutter will allow me to use this as a template for future labs. Really enjoyed the introduction to Tween animatio and stateful widgets. Flutter can simply be explained as a widget tree where each instance branches off to a different flow but can be called back once you're in a children widget. Like a river flowing up and downstream at the same time.

## Observations
- AnimationController can be used to run any animation
- AnimatedBuilder rebuilds the widget tree when the value of an Animation changes
- Using a Tween, you can interpolate between almost any value, in this case Color

For more information refer to the official documentation.

- [Flutter Documentation](https://docs.flutter.dev/)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Flutterfire](https://firebase.google.com/docs/flutter/setup?platform=ios)
- [Google's awesome Flutter Youtube channel, Lots of great content here](https://www.youtube.com/channel/UCwXdFgeE9KYzlDdR7TG9cMw)

---

## Demo
![HomePage Gif](https://github.com/C-Dev66/SignInScreen/blob/main/screenshots/SignInScreenGif.gif)

