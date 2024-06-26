# Exploring SwiftUI

## [Slides](https://tech-at-du.github.io/ACS-1410-Introduction-to-Swift/Slides/05-SwiftUI1/README.html ':ignore')

<!-- > -->

## Learning Objectives

By the end of this lesson, students should be able to:

- Familiarize with Apple's frameworks for UI
- Explain what is SwiftUI and how it works with Declarative syntax
- Build layouts using stacks
- Create views efficiently using Swift's constructs

<!-- > -->

## Frameworks for UI

- [UIKit](https://developer.apple.com/documentation/uikit)
- [SwiftUI](https://developer.apple.com/documentation/swiftui/)

<!-- > -->

## SwiftUI

![swiftui](assets/swiftui.png)

SwiftUI is an innovative way to build user interfaces across all Apple platforms using Swift.  

<!-- > -->

## Declarative syntax

*Declarative programming is a non-imperative style of programming in which programs describe their desired results without explicitly listing commands or steps that must be performed.*

Telling SwiftUI **what** we want the UI to look like and work, then it figures out **how** to make that happen.  

- Easy to read
- Natural to write

<!-- > -->

## UIKit and SwiftUI

Side by Side

<div id="left">

![homecook](assets/homecook.jpg)
</div>

<div id="right">

![chef](assets/chef.jpg)
</div>
<!-- home cook needs all instructions and steps vs professional cook who can make a dish with just the name -->

<!-- > -->

## Design Tools

With Xcode 11 came a lot of new tools to work with SwiftUI.

As we work in the code editor, we get to see a live preview of the app.

As we work in the design canvas, everything we edit is in sync with the code editor.

In any case, Xcode recompiles the changes instantly and inserts them into a running version of your app, visible, and editable at all times.

<!-- > -->

## Some facts

- SwiftUI runs on iOS 13, macOS 10.15, tvOS 13, and watchOS 6. And future versions of each.
- SwiftUI is faster than UIKit.
- You can have a project than mixes SwiftUI and UIKit.
- SwiftUI does not replace UIKit.

<!-- > -->

## What should we learn?

For now SwiftUI has limited API coverage, limited adoption and support.

It will be a big deal in years to come (maybe 2 or 3). But as iOS developers in the job industry **now**, we need to know about UIKit as a requirement.

The best option is to learn SwiftUI on the side as well.

<!-- > -->

## Stacks 📚

[designcode.io explanation for stacks](https://designcode.io/swiftui-handbook-hstack-vstack)

<!-- > -->

## Live demo

1. Finding the preview
1. Template contents
1. Hello world
1. Hello world in an HStack
1. Hello world in a VStack
1. Grid with text
1. Add image
1. Simulator

A view is a rectangular area on the screen where we can display content and interact with it.

In the template contents we have `body` that behaves like a view.

No change needed

```Swift
   HStack{
    Text("Hello World")
    Text("Hello World")
    Text("Hello World")
   }
```

```swift
   VStack(spacing:10){
    Text("Hello World")
    Text("Hello World")
    Text("Hello World")
   }
```

```swift
   VStack(spacing:30){
    HStack(spacing:30){
      Text("👩🏻‍💻")
      Text("👩🏾‍💻")
      Text("👨🏽‍💻")
      Text("👨🏻‍💻")
    }
    HStack(spacing:30){
      Text("👩🏻‍💻")
      Text("👩🏾‍💻")
      Text("👨🏽‍💻")
      Text("👨🏻‍💻")
    }
   }
```

```swift
    Image("01")
      .resizable()
      .scaledToFit()
      .frame(width: 100, height: 100)
```

<!-- > -->

## Warmup

<div id="left">

- Replicate this layout and write your own text at the bottom.
- Find the thread in our Slack channel and post a screenshot when you are done.
</div>

<div id="right">

![warmup](assets/warmup.png)
</div>

<!-- > -->

## In Class Activity

Create the weather app. Create as much of this layout as you can. Concetrate on the top of the Screen. 

![weather](./assets/weather.png)

The top of the screen shows The location, temperature, and a description of the the weather. These are in a vertical stack. Each element has a different font size. 

Create a new Xcode project. 

Choose SwiftUI as the interface. 

Open `ContentView.swift` in the editor. Everything you do will happen in the first struct. Notice there are two structs. The second struct is responsible for drawing the preview, you will not be editing this! All edits will happen in the `struct ContentView` 

```Swift
struct ContentView: View {
  var body: some View {
    VStack {
      Text("Cupertino")
      Text("70˚")
      Text("Partly Cloudy")
    }
  }
}
```

This should show a vertical list of text elements. 

Use modifiers to set the size of these elements. 

```Swift 
struct ContentView: View {
  var body: some View {
    VStack {
      Text("Cupertino")
        .font(.system(size: 24))
      Text("70˚")
        .font(.system(size: 60))
      Text("Partly Cloudy")
    }
  }
}
```

`Text().font(.system(size: 24))` is a modifer that sets the size of the font. 

You adjust these until they look best to you.

Beneath the description There is a row with "H: 85˚ L: 55˚". While this could be a single line of text, if it was multiple `Text` elements they could be contained in an `HStack`. Try this. 

```Swift 
struct ContentView: View {
  var body: some View {
    VStack {
      Text("Cupertino")
        .font(.system(size: 24))
      Text("70˚")
        .font(.system(size: 60))
      Text("Partly Cloudy")
      // Add this v
      HStack {
        Text("H: 85˚")
        Text("L: 55˚")
      }
    }
  }
}
```

Notice the `HStack` was added inside the existing `VStack`

```Swift
VStack {
  ...
  // Add this v
  HStack {
    ...
  }
}
```

Let's add a background. Use the image here: 

![weather-bg](./assets/weather-bg.png)

To stack things front to back you'll use a `ZStack`. To display an image you'll use the `Image` element. 

Download the image above or use one of your own.

Drag the image into the `Assets.xcassets` of your Xcode project. You'll see this in the file list below `ContentView.swift`. 

Next embed everything in a `Zstack`. You'll use the `Image` element to add the image. 

```Swift
struct ContentView: View {
  var body: some View {
    ZStack {
      Image("weather-bg")
      
      VStack {
        Text("Cupertino")
          .font(.system(size: 24))
        Text("70˚")
          .font(.system(size: 60))
        Text("Partly Cloudy")
        // Add this v
        HStack {
          Text("H: 85˚")
          Text("L: 55˚")
        }
      }
    }
  }
}
```

The `Image("name-image-asset")` uses the name of the image in the Assets.xcassets. Make sure these match. My image was named `weather-bg`. 

Notice that the `ZStack` is the parent of the `VStack` that had been the top level element previously. 

```Swift
ZStack {
  Image("weather-bg")
  
  VStack {
    ...
  }
}
```

To get the image to fill the space you'll need to add some modifers. 

```Swift
Image("weather-bg")
  .resizable() // make the image resizable
  .aspectRatio(contentMode: .fill) // make the image fill the space
```

While this looks good so far. With the background the text might look better in white. You can add modifers to the text elements to any element to set the fore ground color like this: 

```Swift
Text("Cupertino")
  .font(.system(size: 24))
  .foregroundColor(.white)
```

While that would work it would be tedious since you'd need to add a modifer for each text element. 

Better, in this case is to add the modfier to a parent. This way the children will inherit the modifer. 

```Swift
struct ContentView: View {
  var body: some View {
    ZStack {
      Image("weather-bg")
        .resizable()
        .aspectRatio(contentMode: .fill)
        .frame(alignment: .topLeading)
      
      VStack {
        Text("Cupertino")
          .font(.system(size: 24))
        Text("70˚")
          .font(.system(size: 60))
        Text("Partly Cloudy")
        // Add this v
        HStack {
          Text("H: 85˚")
          Text("L: 55˚")
        }
      }
    }
    .foregroundColor(.white) // Add this!!!!!!
  }
}
```

Here the modifer added to the `ZStack` sets the foreground color for all of the inner elements. 

```Swift
ZStack {
  ...
  VStack {
    ...
    HStack {
      ...
    }
  }
}
.foregroundColor(.white)
```

This shows the stack structure with the modifer. 

Like components in react, if you're familiar, SwiftUI Views can be be broken out into separate subviews. Imagine you want to break out the Weather display from the background image and ZStack. 

Create a new SwiftUI subview like this. You can add the following in the same file but outside the existing code blocks. Start with: 

```Swift 
struct WeatherView: View {
  var body: some View {

  }
}
```

Notice this new view is the same base structure as `ContentView` but has a different name. XCode will show an error until this view renders a view element. 

Cut the `VStack` and everything in it from inside of the `ZStack` in `ContentView`. 

This should give you something like this: 

```Swift
struct WeatherView: View {
  var body: some View {
    VStack {
      Text("Cupertino")
        .font(.system(size: 24))
      Text("70˚")
        .font(.system(size: 60))
      Text("Partly Cloudy")
      // Add this v
      HStack {
        Text("H: 85˚")
        Text("L: 55˚")
      }
    }
    .foregroundColor(.white)
  }
}

struct ContentView: View {
  var body: some View {
    ZStack {
      Image("weather-bg")
        .resizable()
        .aspectRatio(contentMode: .fill)
        .frame(alignment: .topLeading)
    }
  }
}
```

Be careful of the curly braces. It can be tricky to find the matching braces! 

Notice there are two structs, SwiftUI views are defined as structs, `WeatherView` and `ContentView`. 

To use the new `WeatherView` in the `ContentView` add it below the `Image` like this. 

```Swift
struct ContentView: View {
  var body: some View {
    ZStack {
      Image("weather-bg")
        .resizable()
        .aspectRatio(contentMode: .fill)
        .frame(alignment: .topLeading)
      
      WeatherView() // Add the WeatherView here!!!!!
    }
  }
}
```

The each of the two views is now simplified. You can also move these views into seprate Swift files to organize them. 

Views can also receive parameters from outside to pass data into the view that can be displayed. Give this a try by passing the temperature into the `WeatherView`. 

Parameters in SwiftUI Views are defined like variables. Define a `temp` var in `WeatherView`. 

```Swift
struct WeatherView: View {
  var temp: String // Add a new param here!!!!
  var body: some View {
    ...
  }
}
```

Use that parameter to set the temp strin inside the view. 

```Swift
struct WeatherView: View {
  var temp: String

  var body: some View {
    VStack {
      Text("Cupertino")
        .font(.system(size: 24))
      Text("\(temp)˚") // Add temp here!!!!!
        .font(.system(size: 60))
      Text("Partly Cloudy")
      HStack {
        Text("H: 85˚")
        Text("L: 55˚")
      }
    }
    .foregroundColor(.white)
  }
}
```

To pass the a value you will need to add the new parameter where the instance of the view is created. You'll be seeing an error until you do that!

```Swift
struct ContentView: View {
  var body: some View {
    ZStack {
      Image("weather-bg")
        .resizable()
        .aspectRatio(contentMode: .fill)
        .frame(alignment: .topLeading)
      
      WeatherView(temp: "72")
    }
  }
}
```

<!-- > -->

## Adding it to an existing project.

If you need to add the ViewController you created with SwiftUI, you can use it as a regular view in a project that mostly uses UIKit, using the class [UIHostingController](https://developer.apple.com/documentation/swiftui/uihostingcontroller).

You will need to add the SwiftUI file to the project.

Then just use it as a regular view with the help of the class

```swift
let swiftUIView = ContentView()
let viewController = UIHostingController(rootView: swiftUIView)
```


## Additional Resources

- [What is SwiftUI](https://developer.apple.com/xcode/swiftui/)
- [SwiftUI tutorials](https://developer.apple.com/tutorials/swiftui/tutorials)
- [100 days of SwiftUI](https://www.hackingwithswift.com/100/swiftui)
- [SwiftUI by examples](https://www.hackingwithswift.com/quick-start/swiftui)
- [Learn App Making - SwiftUI intro](https://learnappmaking.com/swiftui-getting-started-how-to-ios-swift/)
- [Warmup Images](https://www.sketchappsources.com/free-source/4389-coronavirus-icons-sketch-freebie-resource.html)
- [Let's build that app - Calculator](https://www.youtube.com/watch?v=ULEFrRSPXFE)
