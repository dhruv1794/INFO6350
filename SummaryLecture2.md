# Discussion


1. [Android Architecture](https://sites.google.com/view/mobileappdev/home/androidarchitecture?authuser=0)
2. What is JVM ? 
3. [What is Android Run Time?](https://developer.android.com/guide/platform)
4. [IOS Architecture](https://sites.google.com/view/mobileappdev/home/androidarchitecture/iosarchitecture?authuser=0) -> Naming conventions are different, No hardware transparency
5. SandBoxing Application - Linux creates sandboxes for every application. (Android Kernel). The way they do this is by creating a unique ID for every Application. A sandboxes gives you your own instance of file System. Every application has its own process. Two applications cannot access each other’s file system or processes. All resources are divided (distributed). Merit -> If one application crashes , it will not affect other applications. IOS uses the same concept but it is not transparent.  This makes it very stable, create memory boundaries. This is not the case for Windows laptops or even MacOS. This is done to support limited resources on Mobile phones
6. Android App Basics -> Architectural diff between iOS and Android. There is just not one entry point , ( unlike java which has just one entry point -> main()) . Eg: Address Book on phone -> Whatsap WeChat all share contacts on the phone internally.(native applications are triggered through other applications ) , Photos Applications.
7. *Priority Model* -> Priority can be assigned to every thread on linux. We have something similar here.  Android , iOS Priorities -> [ Critical, High, Lower ] 
    - *Critical* -> On the screen application -> OS focus is to make sure application currently used has most resources, because otherwise it is a bad UX (ANR -> Application not responding , This happened for first 5-6 years
    - *Lower* -> Detecting Malware, Auto Responding Messaging
    - *High* -> All open Applications 
    - [Link](https://sites.google.com/view/mobileappdev/home/android-app-basic?authuser=0)
8. OOM Pillar Algo -> Out of Memory [ It monitors RAM, and adjust priorites ]. Application that is running for longest time is killed first by this Algorithm when there is shortage of Resources.
9. [IOS Basics](https://sites.google.com/view/mobileappdev/home/android-app-basic/ios-app-basics?authuser=0) 
    - ***Most Critical Part***
    1. [Entitlements](https://developer.apple.com/documentation/bundleresources/entitlements) ,
    2. [Info.plist ](https://developer.apple.com/documentation/bundleresources/information_property_list)


`Break Time`

1. [Android Life Cycle](https://sites.google.com/view/mobileappdev/home/android-activity?authuser=0) -> 
- 3 States 
- Active/Running   
- Stopped
- Paused -> Eg: on Screen but not taking any user input. -> When the keyboard is up, application is visible but the app is not interactive, only keyboard is active/ interactive. Eg 2: Dialog box pops open on an application.
2. Life Times
-  3 Lifetimes
 - Full Time ( onCreate(), onDestroy())
 - Visible ( onStart(), onStop()) -
 - Foreground ( onResume() , onPause())
￼

Notes: Bubbles are different states. 
---
Notes: Today’s phones are much more powerful and hence you won’t notice application killing. If you want to notice the killing of applications -> Go to Xcode , connect your device-> see logs
---
Notes: Developer responsibility to prevent memory leaks and perform cleanups.
---

3. Life Cycle Methods -` onCreate()`,` onDestroy()`, `onStart()`, `onStop()`, `onResume()` , `onPause()`

### Email Application Walkthrough Example

 - When Inbox Activity is launched (3 lifecycle methods are called) -> onCreate(), onStart(), onResume()
 - What would you do during onCreate() -> Check Internet, Retrieve email (server call), check authentication, 
 - When another email obscures the application onStop() life cycle method is called (Got a incoming call, or called someone)
 - When the call ends -> Application must remember user State. , check if user is still logged-in. ( why? -> what if password is changed when on call? ), poll for email again. -> onResume LifeCycle is called.
- Implement all logic for data retrieval in onStart(), and pass it to its children Widgets. 
 - onPause() is called during search, creating email, -> Eg: News Notification 
 - onResume() -> make sure user state is maintained.
 - OnResume() has a small problem, in the Visible LifeTime Any server which takes time.  We have to handle new Data calls in the background or the user experience is compomised. We should not duplicate the code. We can duplicate the execution. Which means write one function and use it in multiple places. 

Composing Email-> New Screen

 - onCreate() -> When you start typing email to send the mail to -> we do a server call to fetch information.
 - onStart()-> 
 - onPause() -> When typing (keyboard is active, whereas app is in pause state) -> Preserve state of the app continously. 
 - onResume() -> Retrieve user state saved onPause()
 - onStop() -> Should draft the application and save it the cloud to retain user information. We don’t want user to loose information. 

 Notes: Multi Devices which have logged in to the same email can be synced through cloud . Checkout out Firebase.
 ---
 - Send button click should check if user(Satyam :p) is still authenticated.
 - Perform memory clean ups in onDestroy()

 - Another Example is Netflix . Try working it out, think of ways you would create this application and what functions would you call on different lifecycle function.

 - Bank Applications would log you out every time you are onDestroy() 

Every Application use-case is different. 


Doubts


 - Payment Question -> 
For small businesses, PCI compliance involves requirements such as encryption of cardholder data, managing firewalls, updating antivirus software and assigning unique IDs to each person with computer access.



