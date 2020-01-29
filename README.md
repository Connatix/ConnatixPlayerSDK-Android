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
    implementation 'com.connatix.sdk:connatixplayersdk:1.1.5'
}
```
### Manually
If you prefer not to use Maven dependency manager, you can integrate Connatix Player SDK into your project manually.
## Using the SDK
### Elements
```kotlin
//New player instance
var elementsPlayer = ElementsPlayer(this, null, 0,this)
// privacySharedPreferencesName is the name of the SharedPreferences where you store CCPA info
//Insert player as a subview
var params : LinearLayout.LayoutParams = LinearLayout.LayoutParams(
            LinearLayout.LayoutParams.MATCH_PARENT,
            LinearLayout.LayoutParams.MATCH_PARENT)
elementsPlayer.layoutParams = params
sdkContainerView.addView(elementsPlayer)
 
//Config object example
val appSettings = AppSettings("https://example.com","https://examplestore.com/app", listOf("health", "finance"),true,false)
val playerConfig = ElementsConfig("e9009be9-c5db-4ac0-b00a-119c159bbff5", appSettings)
 
//Player setup
elementsPlayer.setupPlayer(config: playerConfig)

//Listen for events
elementsPlayer?.listenFor(EventType.volumeChanged,true)
```
### Playspace
```kotlin
//New player instance
var playspacePlayer = PlayspacePlayer(this, null, 0, this)
// privacySharedPreferencesName is the name of the SharedPreferences where you store CCPA info
//Insert player as a subview
var params : LinearLayout.LayoutParams = LinearLayout.LayoutParams(
            LinearLayout.LayoutParams.MATCH_PARENT,
            LinearLayout.LayoutParams.MATCH_PARENT)
playspacePlayer.layoutParams = params
sdkContainerView.addView(playspacePlayer)
 
//Config object example
val appSettings = AppSettings("https://example.com","https://examplestore.com/app", listOf("health", "finance"),true,false)
val playerConfig = PlayspaceConfig("3d097366-2276-4c4b-b564-3cbd9b6c30cd", "5bd62672-d010-47f0-bab2-145b331085c6", appSettings)
 
//Player setup
playspacePlayer.setupPlayer(config: playerConfig)

//Listen for events
playspacePlayer?.listenFor(EventType.changeSlide,true)
```
## Requirements
* minSdkVersion 19
* Android Studio 3.4+
* Kotlin 

