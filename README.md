# LinkedinSwift

[![CocoaPods](https://img.shields.io/cocoapods/v/LinkedinSwift.svg)](https://github.com/tonyli508/LinkedinSwift.git)


LinkedinSwift is a project for managing native LinkedIn SDK using [Cocoapods](https://cocoapods.org)

Linkedin Oauth Helper, depend on Linkedin Native App installed or not, using Linkdin IOS SDK or UIWebView to login, support Swift with iOS 7

Latest version 1.4 is based on [LinkedIn SDK 1.0.4](https://content.linkedin.com/content/dam/developer/sdk/iOS/li-ios-sdk-1.0.6-release.zip) and [IOSLinkedinAPI for webview auth](https://github.com/jeyben/IOSLinkedInAPI).

## How to use

```ruby
pod 'LinkedinSwift', '~> 1.4'
```

Check out Example project.

- Setup configuration and helper instance.
```swift
let linkedinHelper = LinkedinSwiftHelper(configuration: LinkedinSwiftConfiguration(clientId: "77tn2ar7gq6lgv", clientSecret: "iqkDGYpWdhf7WKzA", state: "DLKDJF45DIWOERCM", permissions: ["r_basicprofile", "r_emailaddress"]))
```
- Setup Linkedin SDK settings: [instruction here](https://developer.linkedin.com/docs/ios-sdk)

- Login:
```swift

		linkedinHelper.authorizeSuccess({ (lsToken) -> Void in
            //Login success lsToken
        }, error: { (error) -> Void in
            //Encounter error: error.localizedDescription
        }, cancel: { () -> Void in
            //User Cancelled!
        })
```
- Fetch profile:
```swift

		linkedinHelper.requestURL("https://api.linkedin.com/v1/people/~?format=json", requestType: LinkedinSwiftRequestGet, success: { (response) -> Void in
            
            //Request success response
            
        }) { [unowned self] (error) -> Void in
                
            //Encounter error
        }
```

Example project screenshots:

<p align="center">
<img src="https://github.com/tonyli508/LinkedinSwift/blob/master/page_images/screenshot1.jpg" alt="Demo photo" width="56" height="100" />
</p>

## Known issues

~~It turns out Linkedin 1.0.6 release note: `Added Bitcode support.` is a lie.~~ (They secretly remove 1.0.6) You need to turn off Bitcode to make it work.

