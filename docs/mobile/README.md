# Mobile

![Cover](cover.jpg)

Since OSes such as Firefox OS and Windows 10 Mobile come and go in a matter of years (and are hardly used while they're there), we'll only consider Android and iOS.

Here is every way you can make a mobile app. When I use the word _native_, I mean that it's been created using the officially recommended technologies (e.g., using Swift on iOS).

## Sharing business logic in Kotlin, and writing the platform specifics natively

This is a great choice since you'll already be using Kotlin for Android development. Besides being able to leverage an excellent language and ecosystem for your business logic, you'll also be able to share the same code on other platforms such as the server side.

## Xamarin

Xamarin allows you to share business logic while using first-party tooling to build separate UIs for different platforms. It deploys to Android, iOS, and UWP. They also allow you to access any native API using a consistent interface through their official C# wrappers which are available within a few days of new features being released on their respective platforms. Of course, certain aspects such as your app's size and native tooling will be less than optimal. You should use Xamarin if you have the resources for C# and Xamarin, but not Kotlin and Swift. Xamarin will obviously require you to know a certain amount of platform specifics, but the learning curve is relatively low. When I say using Kotlin, I mean using it to write not only the native Android UI, but the shared business logic as well.

## Building both Android and iOS apps natively

This is great if you don't have the resources to share business logic in Kotlin, but have the resources to natively build and maintain the app on two different platforms.

## Building only an Android app natively

This is great if the vast majority of your target audience uses Android, and you're short on resources.

## Building only an iOS app natively

This is great if the vast majority of your target audience uses iOS, and you're short on resources.

## Flutter

Flutter is seriously lacking in both the UI and business logic aspects, and will clearly not improve noticably in the foreseeable future. It requires you to be an expert in platform specifics. Unlike Xamarin which provides C# wrappers and official documentation for each platform's API, Flutter requires you to have advanced knowledge of not only its own framework, but the platforms as well. Since you'll have to write native code for even the most trivial aspects of your application, you'll have to be an expert in Kotlin, Swift, Android documentation, iOS documentation, Android project structures, iOS project structures, Android tooling (you'll need to learn and configure complex plaform-specific build systems such as Gradle yourself since you'll need to download the relevant official or third-party libraries), and iOS tooling. Clearly, Flutter falsely advertises that it speeds up app development time while helping you build a better app. The opposite is true. Flutter takes significantly longer to write an app than building it natively in Android and iOS. And after all that extra effort in learning a third platform (Dart, Flutter, and the relevant tooling), you end up with a significantly worse app (which includes pseudo-native UI components and a bloated app size).

- The idea is to share the business logic in Dart. Dart has a pathetic ecosystem, and its features are significantly worse than the platform-natives (i.e., Kotlin and Swift).
- Unlike in Xamarin where the UI must be written twice for each platform, Flutter allows you to share common UI code. However, this causes the UI to strongly disagree with the most basic principles on the other platform. Android's Material Design has a strong contrast with iOS's Cupertino in everything from gestures and animations, to layouts and widgets. You might think this a nonissue if you were to simply write the UI once for each platform. However, this is not the case. Even basic apps which make no use of remotely platform-specific components (e.g., HTTP API calls, camera access), the app will refuse to run on iOS without even giving an error message. There are many other issues Flutter has with the most basic of UI requirements which you will easily find searching on communities like Reddit.
- Unlike Xamarin, you must use native code for platform APIs. Even though websites can natively access trivial components such as the camera and microphone, Flutter simply cannot. What's worse is that even platform-specific software components such as notifications require native code, and they lack official- or community-created plugins, so you'll have to write them yourself. 

## Sharing business logic in C/C++, and writing the platform-specifics (e.g., the UI) natively

This was never a good choice, and is now a bad one considering that you can use Kotlin instead. C/C++ are primitive languages which require a relatively steeper learning curve, require libraries for the most basic of operations, and mandate that the native code calling it create wrappers in order to use them. For these reasons and more, companies such as [Dropbox](https://insights.dice.com/2019/08/27/swift-kotlin-c-dropbox-native/) and [Slack](https://slack.engineering/client-consistency-at-slack-beyond-libslack-c9cfbe778fb7) have emigrated from this approach.

## Hybrid 

Hybrid (e.g., React Native, Ionic) apps make use of web standards to create cross-platform apps. These solutions are only adopted because they have a smaller learning curve if you already know frontend web development. Otherwise, they scale poorly because they cannot access native platform features (e.g., AR), and have a seriously lacking ecosystem. The ecosystem will never improve because web technologies were meant to be used on..the web (surprise, surprise), and there are too many hybrid toolchains at any given time (e.g., Angular). Web technologies were not meant for mobile development, and hence perform poorly at it; you shouldn't use a language meant for DOM manipulation in the browser. As with any technology significantly worse than the one meant for the task at hand, but are adopted for its unworthy slightly lower learning curve, learning the recommended technology scales much better (e.g., [Udacity and Airbnb](https://adtmag.com/articles/2018/07/10/abandon-react-native.aspx) emigrated from React Native).

## Writing a mobile-friendly website (not a PWA)

This is an easy choice without the demerits of a hybrid app approach. Since this is a regular website, it will run on desktops (via a browser) as well, and the lack of a platform-conforming UI is a nonissue. Of course, it will be used less due to the lacking UX (compared to native apps), and you won't be able to access any nontrivial platform features (the web only grants access to small platform components such as the camera, not the full filesystem or notification bar).

## PWAs 

Websites are not meant to be used as mobile apps. They are even worse than hybrid apps since the UI is completely non-native, and they lack any tooling whatsoever. Your entire development time will go into using an ecosystem which wasn't designed for the task at hand, all while gaining access to zero new platform features (when compared to a non-PWA website). The technologies behind PWAs such as caching are excellent for websites, but do not make it anywhere near a good fit for a mobile app present on the user's home screen. The only use case for building a PWA is if you want to distribute an app on iOS, but don't have the resources (e.g., money, hardware, skills, time) for it. In this case, you should be building a mobile-friendly website, and using the PWA feature as an easier way to launch the website. PWAs will never be a subsitute, not even a poor one, for mobile app development.