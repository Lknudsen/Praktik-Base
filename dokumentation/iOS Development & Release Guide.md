# iOS Development & Release Guide (React Native)

This document describes how we develop, test, and release our **React Native app (PK) for iOS**, when development is primarily done on Windows and iOS builds must be performed on macOS.

It covers:
- Mac setup (local vs cloud)
- Xcode configuration
- iPhone Developer Mode
- TestFlight
- App Store release



## 1. Architecture overview

Apple requires iOS apps to be built on macOS.  
Our setup is therefore split:


Windows developers (React Native)
        
Git repository
        
Mac (Xcode build)
        
TestFlight
        
App Store



## 2. Mac setup options

Running MacOS locally on Apple Silicon is a requirement for entering developer mode on an iPhone.
- Performance varies depending on CPU architecture, generation and amount of available memory

Use case
- Developer mode
- Debugging
- Physical device testing
- Xcode

Cloud hosted Mac won't be able to run physical device testing, however it may be an option for multiple developers to build for iOS.
- CI/CD
- iOS builds
- TestFlight uploads
- App store releases

Software requirements for Mac
- Latest version of MacOS
- Xcode (Find it on the App Store)
- Node.js
- Yarn or npm (Required for React Native -> Xcode won't build without it)
- CocoaPods (To manage library dependencies for Xcode projects)
- Apple ID assigned to the developer program
- Testflight (Find it on the App Store)



## 3. Apple developer program

1. Follow the given link: https://developer.apple.com
2. Enroll in the Apple developer program
3. Annual fee required
4. Apple now needs to provide their approval



## 4. App store connect setup
1. Follow the given link: https://appstoreconnect.apple.com
2. My Apps -> New App
3. Platform: iOS
4. Provide bundle ID



## 5. Xcode signing & certificate
- Select app target
- Signing & capabilities
- Select team
- The bundle ID must match App store connect
- Enable "Automatically manage signing"
- Xcode will now handle certificates and provisioning profiles automatically
- To install iOS dependencies run the following: "cd ios"



## 6. Test iPhone
A personal iPhone can be used as a test device as no personal data will be erased, however it is highly recommended to backup your data before entering developer mode.
1. Connect test iPhone to your local machine running MacOS
2. Enter settings on your iPhone -> Privacy & Security -> Enable developer mode
3. Restart the iPhone
4. Xcode -> Window -> Devices and Simulators -> Trust the device if prompted.

To run the app on Xcode
- Select iPhone as destination
- Run



## 7. Testflight
TestFlight is the official online service from Apple, which allows developers to distribute beta versions of software to be tested prior to releasing the app on the App Store
- Xcode -> Product -> Archive
- Upload to App Store Connect

Internal testing
- App Store Connect -> TestFlight
- Add testers
- Send invitations



## 8. App Store release
1. Fill in metadata
2. Upload screenshots
3. Complete the privacy details
4. Select build
5. Submit for review
6. Wait for approval prior to release