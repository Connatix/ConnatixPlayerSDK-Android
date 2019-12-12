## Introduction
Connatix Player SDK provides a native way to deliver successful video experiences to publishers on Android. 
## Installation
### Gradle & Maven
The Android SDK can be integrated into projects using [Gradle](https://gradle.org) build tool and [Maven](http://maven.apache.org) dependency manager.
To integrate Connatix Player SDK into your Android project, specify the Maven repo path in your project's `build.gradle`:
```ruby
allprojects {
    repositories {
        google()
        jcenter()
         
        // Path to Maven repo
        maven{
            url "https://dl.bintray.com/connatix/ConnatixPlayer"
        }
    }
}
```
To finish, in the app's `build.gradle` file, add the SDK as a dependency:
```ruby
dependencies {
    implementation 'com.connatix.sdk:connatixplayersdk:1.0.9'
}
```
### Manually
If you prefer not to use Maven dependency manager, you can integrate Connatix Player SDK into your project manually.
## Using the SDK
```kotlin
//New player instance
var connatixPlayer = ConnatixPlayerSDK(context:this, attrs:null, defStyleAttr:0, privacySharedPreferencesName: "appsPrivacySettingsPrefs" delegate:this)
// privacySharedPreferencesName is the name of the SharedPreferences where you store CCPA info
//Insert player as a subview
var params : LinearLayout.LayoutParams = LinearLayout.LayoutParams(
            LinearLayout.LayoutParams.MATCH_PARENT,
            LinearLayout.LayoutParams.MATCH_PARENT)
connatixPlayer.layoutParams = params
sdkContainerView.addView(connatixPlayer)
 
//Config object example
val appSettings = AppSettings("https://example.com","https://examplestore.com/app", listOf("health", "finance"),true,false)
val playerConfig = PlayerConfig("cd6bde64-da62-4f4d-bb78-79ec535f1727", appSettings)
 
//Player setup
connatixPlayer.setupPlayer(playerType: PlayerType.Elements, config: playerConfig)

//Listen for events
connatixPlayer?.listenFor(EventType.volumeChanged,true)

```
## Requirements
* minSdkVersion 19
* Android Studio 3.4+
* Kotlin 

