react-native-beautiful-video-recorder
===

The video recorder component that extends from `react-native-camera`. It works for both iOS & Android.

![Sample](Screenshot.PNG)


## Installation

```bash
npm i --save react-native-beautiful-video-recorder
react-native link
```

Please file an issue if you have any trouble!
## Configuration
### iOS
With iOS 10 and higher you need to add the "Privacy - Camera Usage Description" key to the info.plist of your project. This should be found in 'your_project/ios/your_project/Info.plist'. Add the following code:

```
<key>NSCameraUsageDescription</key>
<string>Your message to user when the camera is accessed for the first time</string>

<!-- Include this only if you are planning to use the microphone for video recording -->
<key>NSMicrophoneUsageDescription</key>
<string>Your message to user when the microsphone is accessed for the first time</string>
```

### Android
Add permissions in your Android Manifest (required for video recording feature)

```
<uses-permission android:name="android.permission.RECORD_AUDIO"/>
<uses-permission android:name="android.permission.RECORD_VIDEO"/>
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

## Usage

```jsx
import VideoRecorder from 'react-native-beautiful-video-recorder';
....

start = () => {
	this.videoRecorder.open((data) => {
		console.log('captured data', data);
	});
}

render() {
	return (
		<View>
			......
		  <VideoRecorder ref={(ref) => { this.videoRecorder = ref; }} />
		  <TouchableOpacity onPress={this.start}>
		  	<Text>Start</Text>
		  </TouchableOpacity>
		</View>
	);
}
```
## Callback Data

param | Info
------ | ----
path | Returns the path of the captured image or video file on disk
width | (currently iOS video only) returns the video file's frame width
height | (currently iOS video only) returns the video file's frame height
duration | (currently iOS video only) video file duration
size | (currently iOS video only) video file size (in bytes)

## License

MIT
