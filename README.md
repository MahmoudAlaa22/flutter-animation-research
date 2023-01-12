## 1. Research: Project Title 

- Keywords: 
  - flutter animation
  - flutter animation controller
  - flutter animation example
  - flutter animation examples
  - flutter animation library
  - flutter animation jank
  - flutter animation curves
  - flutter animation package
  - flutter animation tutorial
  - flutter animation widgets
  - flutter animation controller vsync
  - flutter animation loop
  - flutter animation sequence
  - flutter animation takes up resource even when not running
  - flutter animation listener
  - flutter animation controller fling speed
  - flutter animation slow down
  - flutter animation choppy
  - flutter loading animation	
  - FadeInDown Flutter
  - SlideTransition Flutter
  - gesturedetector flutter animation
  - how to do a translate animation in flutter
  - how animation image in decoration in flutter
  - flutter how to replay animation
  - how to make flutter animation
  - lottie flutter	
  - animation flutter	
  
- Video Title:  "Creating Dynamic Animations in Flutter: A Comprehensive Guide to the Flutter Animate Library"


## 2. Research: Competitors

**Flutter Videos/Articles**

- https://pub.dev/packages/flutter_animate (Official package documentation)
- https://blog.gskinner.com/archives/2022/09/introducing-flutter-animate.html
- https://guillaume.bernos.dev/using-flutter_animate-for-a-flutter-game-animation/


**Android/Swift/React Videos**

- NA

**Great Features** 
- Pre-built effects such as fade, scale, slide, flip, blur, shake, shimmer, shadows, and color effects (saturation and tint)
- Easy to use API that eliminates the need to fuss with AnimationController and StatefulWidget
- Simplified animated builders
- Synchronize animations to scroll, notifiers, or anything
- Integrated events
- Possibility to create custom effects.
**Problems from Videos** 
- NA

**Problems from Flutter Stackoverflow**

- https://stackoverflow.com/questions/74719732/how-to-animate-multiple-children-while-scrolling-using-flutter-animate-package
- https://stackoverflow.com/questions/74977927/how-to-restart-an-animation-with-flutter-animate

## 3. Video Structure

**Main Points / Purpose Of Lesson**

1. Understanding the power and capabilities of the Flutter Animate library for creating dynamic animations in your Flutter app.
2. Main points:
    - Overview of the pre-built effects and their usage
    - How to use the simplified animated builders and create custom effects
    - Synchronizing animations with other widgets and integrated events
3. "In this video lesson, we will be diving into the Flutter Animate library and exploring its various features to create dynamic and visually stunning animations in your Flutter app. From pre-built effects to custom animations and synchronization, we will cover it all. Join us as we learn how to take your Flutter app to the next level with the Flutter Animate library."

**The Structured Main Content**
1. Introduction to the Flutter Animate library
    - Overview of the features and capabilities
    - How to install and set up the library
    * For using the ```flutter_animate``` we need to add this package
    ```yaml
    flutter_animate: ^2.1.0
    ```
2. Using pre-built effects
    - Overview of available effects (fade, scale, slide, flip, blur, shake, shimmer, shadows, and color effects)
    - Example  
    ```dart
    Text("Hello World!").animate()
    .fadeIn() // uses `Animate.defaultDuration`
    .scale() // inherits duration from fadeIn
    .move(delay: 300.ms, duration: 600.ms) // runs after the above w/new duration
    .blurXY() // inherits the delay & duration from move
    ```
3. Creating custom effects
    - Overview of the simplified animated builders
    - How to create and implement custom effects\
        For example, this would add a background behind the text and fade it from red to
        blue:

        ``` dart
        Text("Hello World").animate().custom(
        duration: 300.ms,
        builder: (context, value, child) => Container(
            color: Color.lerp(Colors.red, Colors.blue, value),
            padding: EdgeInsets.all(8),
            child: child, // child is the Text widget being animated
        )
        )
        ```
        `Animate` can be created without a child, so you use `CustomEffect` as a
        simplified builder. For example, this would build text counting down from 10,
        and fading out:

        ``` dart
        Animate().custom(
        duration: 10.seconds,
        begin: 10,
        end: 0,
        builder: (_, value, __) => Text(value.round()),
        ).fadeOut()
        ```
    - How to create and implement toggle effect
     `ToggleEffect` also provides builder functionality, but instead of a `double`,
        it provides a boolean value equal to `true` before the end of the effect and
        `false` after (ie. after its duration).

        ``` dart
        Animate().toggle(
        duration: 2.seconds,
        builder: (_, value, __) => Text(value ? "Before" : "After"),
        )
        ```

        This can also be used to activate "Animated" widgets, like `AnimatedContainer`,
        by toggling their values with a minimal delay:

        ``` dart
        Animate().toggle(
        duration: 1.ms,
        builder: (_, value, __) => AnimatedContainer(
            duration: 1.seconds,
            color: value ? Colors.red : Colors.green,
        ),
        )
        ```
