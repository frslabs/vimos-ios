# Vimos iOS SDK

The Vimos iOS SDK is a realtime Video KYC solution for iOS in **Swift**

![version](https://img.shields.io/badge/version-v1.0.0-blue)

You can find the release history at [Changelog](CHANGELOG.md)

# Table Of Content

- [Prerequisite](#prerequisite)
- [Requirements](#requirements)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Vimos Error Codes](#captus-error-codes)
- [Help](#help)

## Prerequisite

You will need a valid license and Netrc credentials to use the Vimos SDK, which can be obtained by contacting support@frslabs.com. 

Once you have the license , follow the below instructions for a successful integration of Vimos SDK onto your iOS Application.

## Requirements

- Swift 5.0
- iOS 13.0+

## Installation

### Cocoapods


You can use [CocoaPods](http://cocoapods.org/) to install `vimos` by adding it to your `Podfile`:

```ruby
source 'https://gitlab.com/frslabs-public/ios/vimos-ios'
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '13.0'
target '<Your Target Name>' do
use_frameworks!
pod 'Vimos',  ‘1.0.0’
end
```

###### Save/Edit Netrc settings to install custom pod

You will need a valid netrc credentials to install vimos from maven, which can be obtained by contacting `support@frslabs.com`. 

1. Create or edit .netrc file under current user's home directory
2. Write the below lines into that file, replace <YOUR_USERNAME> and <YOUR_PASSWORD> with your credentials which is shared through email and save the file.
```ruby
machine vimos-ios.repo.frslabs.space
login <YOUR_USERNAME>
password <YOUR_PASSOWRD>
```
3. In terminal enter below command to install the pod

   pod install or pod update.

4. Connect with physical device to build and run vimos, It will not build/run in simulator due to camera dependency.

To get the full benefits import `vimos` wherever you import UIKit

``` swift
import UIKit
import Vimos
```

## Getting Started

### Swift

1. Invoke Vimos SDK

```swift
    // ...
    
    override func viewDidAppear(_ animated: Bool) {
        let kyc = KycController(delegate: self)
        kyc.modalPresentationStyle = .fullScreen
        kyc.url = "ENTER URL"
        kyc.licenceKey   = "ENTER LICENSE KEY"
        present(kyc, animated: false)
      }
    // ...    
```

2. Handling the result and import delegate VimosResponseDelegate

```swift
class YourViewController: UIViewController,VimosResponseDelegate {

   func vimosController(_ callerContoller: KycController, didFinishWithResults results: VimosResults) {
        print("VIMOS : SUCCESS")
    }
    func vimosController(_ callerContoller: KycController, didFailWithError error: Int) {
        print("VIMOS : FAILURE")
    }
  
}
```

 ## Vimos Error Codes

   Following error codes will be returned on the `didFailWithError` method of the callback

   | CODE | DESCRIPTION                  |
   | ---- | ---------------------------- |
   | 1001  | Vimos SDK License has expired             |
   | 1002  | Vimos SDK License is invalid             |
   | 1050  | Invalid Vimos URL provided         |
   
   
   Sets the Vimos SDK apiCredentials . Obtain the appropriate api credentials through a REST API call , for details about the REST API, contact `support@frslabs.com`


   ## Help
   For any queries/feedback , contact us at `support@frslabs.com` 
