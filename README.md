# Dodo, a message bar for iOS / Swift

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)][carthage]
[![CocoaPods Version](https://img.shields.io/cocoapods/v/Dodo.svg?style=flat)][cocoadocs]
[![License](https://img.shields.io/cocoapods/l/Dodo.svg?style=flat)][cocoadocs]
[![Platform](https://img.shields.io/cocoapods/p/Dodo.svg?style=flat)][cocoadocs]
[cocoadocs]: http://cocoadocs.org/docsets/Dodo
[carthage]: https://github.com/Carthage/Carthage

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/buttons/dodo_a_message_bar_for_ios_written_in_swift.jpg' alt='Dodo, a message bar for iOS' width='414'>

This is a UI widget for showing text messages in iOS apps. It is useful for showing short messages to the user, something like: "Message sent", "Note saved", "No Internet connection".

* Dodo includes styles for success, info, warning and error type messages.
* The bar can have buttons with custom tap handlers.
* Bar styles can be customized.
* You can provide custom animations for showing and hiding the bar or use one of the default animation presets.

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/Paintings/alices_adventures_in_wonderland.png'
width='300' alt="Illustration fromAlice's Adventures in Wonderland by John Tenniel" >


> At last the Dodo said, `EVERYBODY has won, and all must have prizes.'

From *Alice's Adventures in Wonderland*.

## Setup

There are two ways you can add Dodo to your project.


**Setup with Carthage (iOS 8+)**

Alternatively, add `github "exchangegroup/Dodo" ~> 2.0` to your Cartfile and run `carthage update`.

**Setup with CocoaPods (iOS 8+)**

If you are using CocoaPods add this text to your Podfile and run `pod install`.

    use_frameworks!
    pod 'Dodo', '~> 2.0'


**Setup in Swift 1.2 project**

Use the [previous version of the library](https://github.com/exchangegroup/Dodo/wiki/Swift-1.2-setup).


## Usage

Add `import Dodo` to your source code if you used Carthage or CocoaPods setup methods.

Dodo is an extension of UIView class. You can reach it by using using the `dodo` property in any instance of UIView or its subclass. It can be, for example, the `view` property of your view controller.


### Show and hide message bar


```Swift
view.dodo.success("Everybody has won and all must have prizes.")
view.dodo.info("Extinction is the rule. Survival is the exception.")
view.dodo.warning("This world is but a canvas to our imagination.")
view.dodo.error("The perception of beauty is a moral test.")

view.dodo.hide()
```

If you are showing the bar in the root view you may need to provide top or bottom layout guides. This will prevent the message bar from overlapping with the status or the tab bar.

```Swift
view.dodo.topLayoutGuide = topLayoutGuide
view.dodo.bottomLayoutGuide = bottomLayoutGuide
view.dodo.success("Success is how high you bounce when you hit bottom.")
```

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/presets/success.jpg'
alt='Dodo success presets' width='414'>

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/presets/info.jpg'
alt='Dodo info presets' width='414'>

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/presets/warning.jpg'
alt='Dodo warning presets' width='414'>

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/presets/error.jpg'
alt='Dodo error presets' width='414'>

### Styling

Set `dodo.style` property to style the message bar before it is shown. See the [styling manual](https://github.com/exchangegroup/Dodo/wiki/Styling) for the complete list of configuration options.

```Swift
// Set the text color
view.dodo.style.label.color = UIColor.whiteColor()

// Set background color
view.dodo.style.bar.backgroundColor = DodoColor.fromHexString("#00000090")

// Close the bar after 3 seconds
view.dodo.style.bar.hideAfterDelaySeconds = 3

// Close the bar when it is tapped
view.dodo.style.bar.hideOnTap = true

// Show the bar at the bottom of the screen
view.dodo.style.bar.locationTop = false
```

### Add buttons or icons

Set `style.leftButton` and `style.rightButton` properties to show buttons or icons.

```Swift
// Use a built-in icon
view.dodo.style.leftButton.icon = .Close

// Supply your image
view.dodo.style.leftButton.image = UIImage(named: "CloseIcon")

// Change button's image color
view.dodo.style.leftButton.tintColor = DodoColor.fromHexString("#FFFFFF90")

// Do something on tap
view.dodo.style.leftButton.onTap = { /* Button tapped */ }

// Close the bar when the button is tapped
view.dodo.style.leftButton.hideOnTap = true
```

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/buttons/left_button.jpg'
alt='Dodo bar with left buttons' width='414'>

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/buttons/left_and_right_button.jpg'
alt='Dodo bar with right and left buttons' width='414'>

### Customize animation

Configure the animation effect of the bar before it is shown. See the [animation wiki page](https://github.com/exchangegroup/Dodo/wiki/Animating) for more information.


```Swift
// Use existing animations
view.dodo.style.bar.animationShow = DodoAnimations.Rotate.show
view.dodo.style.bar.animationHide = DodoAnimations.SlideRight.hide

// Turn off animation
view.dodo.style.bar.animationShow = DodoAnimations.NoAnimation.show
```

### Unit testing

Sometimes it is useful to verify which messages were shown by your app in unit tests. It can be done
by setting an instance of `DodoMock` class to `view.dodo` property.

See the [unit testing manual](https://github.com/exchangegroup/Dodo/wiki/Unit-testing) for more details.


## Demo iOS app

This project includes a demo app.

<img src='https://raw.githubusercontent.com/exchangegroup/Dodo/master/Graphics/dodo_demo_ios_app.jpg' width='414' alt='Dodo message bar demo iOS app'>

## Alternative solutions

Here are some other message bar libraries for iOS:

* [cezarywojcik/CWStatusBarNotification](https://github.com/cezarywojcik/CWStatusBarNotification)
* [frankdilo/FDStatusBarNotifierView](https://github.com/frankdilo/FDStatusBarNotifierView)
* [jaydee3/JDStatusBarNotification](https://github.com/jaydee3/JDStatusBarNotification)
* [KrauseFx/TSMessages](https://github.com/KrauseFx/TSMessages)
* [peterprokop/SwiftOverlays](https://github.com/peterprokop/SwiftOverlays)
* [terryworona/TWMessageBarManager](https://github.com/terryworona/TWMessageBarManager)


## Credits

* Original illustration of Alice's Adventures in Wonderland by John Tenniel, 1865. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Alice_par_John_Tenniel_09.png).
* Drawing of White Dodo byFrederick William Frohawk, 1907. Source: [Wikipedia](http://en.m.wikipedia.org/wiki/File:Dodo_reunion-Rothschild_original.jpg).
* Painting of a dodo by Jan Saverij, 1651. Source: [Wikimedia Commons](https://commons.m.wikimedia.org/wiki/File:Jan_Savery_Dodo.jpg#mw-jump-to-license).
* Painting of a dodo head by Cornelis Saftleven, 1638. Source: [Wikimedia Commons](https://commons.m.wikimedia.org/wiki/File:Saftleven_dodo.jpg#mw-jump-to-license).

## License

Dodo is released under the [MIT License](LICENSE).

