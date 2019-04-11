# AuthorizeMe

**AuthorizeMe** is a mobile library for iOS that designed to easy implementation of authorization with social networks. This repository holds the source code that contain a set of providers that implement the functionality needed to get credentials and information about user from various social services.

## Features

* **No dependency:** AuthorizeMe is a fully Swift framework without any dependency. Use the library without any additional Xcode project configurations after installation.
* **Authorization:** There are two ways to authorize user. Use `SystemProvider` for authorize user with iOS social accounts data. Use `WebProvider` for authorize user with `UIWebView` in case when is not possible to use first way.
* **Custom provider:** Implement own provider if AuthorizeMe does not following social network that needed. It is easy and free.

## Getting Started

### Installation

`CocoaPods` is a dependency manager for Cocoa projects. Install it with the following command:

```bash
$ gem install cocoapods
```

OK So, Facebook.plist need to be added in Project -> Build Phases , as Copy Bundle Ressources
Then make sure it is a valid .plist
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>appId</key>
<string>youappid</string>
<key>redirectUri</key>
<string>https://rubygarage.org/</string>
</dict>
</plist>
</plist>
```

To integrate AuthorizeMe into Xcode project using CocoaPods, specify it in `Podfile`:

```ruby
platform :ios, '10.0'

target 'Target Name' do
    use_frameworks!

    pod 'AuthorizeMe'
    # or 
    # pod 'AuthorizeMe/Facebook'
    # to integrate Facebook only

end
```

Then, run the following command:

```bash
$ pod install
```

### First Look

Firstly, import `AuthorizeMe` framework into class in Xcode project.

````swift
import AuthorizeMe
````

Then, turn logging on for seen error messages of authorization process if needed. Do it in `AppDelegate` class is the best way.

````swift
DebugService.isNeedOutput = true
````

Finally, use `Authorize` manager that authorize user with `SystemProvider` if it possible, but in other case manager authorize user with `WebProvider`.

````swift
Authorize.me.on("Name of social network") { session, error in
    // Do something
}
````

To separate usage of various providers, use `SystemProvider` and `WebProvider` apart.

````swift
let provider = FacebookSystemProvider() 
// or 
// let provider = TwitterWebProvider()

provider.authorize { session, error in
    // Do something
}
````

## Guides

* **[Facebook Provider](https://github.com/rubygarage/authorize-me/wiki/Facebook-Provider)**
* **[Twitter Provider](https://github.com/rubygarage/authorize-me/wiki/Twitter-Provider)**
* **[Google Provider](https://github.com/rubygarage/authorize-me/wiki/Google-Provider)**
* **[Instagram Provider](https://github.com/rubygarage/authorize-me/wiki/Instagram-Provider)**
* **[LinkedIn Provider](https://github.com/rubygarage/authorize-me/wiki/LinkedIn-Provider)**
* **[Custom Provider](https://github.com/rubygarage/authorize-me/wiki/Custom-Provider)**
***
AuthorizeMe library is licensed under the [MIT](https://opensource.org/licenses/MIT) license. See the [LICENSE](https://github.com/rubygarage/authorize-me/blob/master/LICENSE) file for more info.
***
<a href="https://rubygarage.org/"><img src="https://rubygarage.s3.amazonaws.com/assets/assets/rg_color_logo_horizontal-919afc51a81d2e40cb6a0b43ee832e3fcd49669d06785156d2d16fd0d799f89e.png" alt="RubyGarage Logo" width="415" height="128"></a>

RubyGarage is a leading software development and consulting company in Eastern Europe. Our main expertise includes Ruby and Ruby on Rails, but we successfully employ other technologies to deliver the best results to our clients. [Check out our portfolio](https://rubygarage.org/portfolio) for even more exciting works!
