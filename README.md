# WebRTC (for iOS)

https://webrtc.org/native-code/ios/

### 1. Clon 'tools'
	$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git

### 2. Add 'tools' path
	$ export PATH=$PATH:/path/to/depot_tools

### 3. Getting the code
	$ fetch --nohooks webrtc_ios

### 4. Generating Project Files
	// debug build for 64-bit iOS
	$ gn gen out/ios_64 --args='target_os="ios" target_cpu="arm64"'
  
	// debug build for simulator
	$ gn gen out/ios_sim --args='target_os="ios" target_cpu="x64"'

### 5. Compile
	// with ninja
	$ ninja -C out/ios_64 AppRTCMobile
  
	// with Xcode
	$ gn gen out/ios --args='target_os="ios" target_cpu="arm64"' --ide=xcode
	$ open -a Xcode.app out/ios/all.xcworkspace

### 6. Merge 
	lipo -create out/ios_64/WebRTC.framework/WebRTC out/ios_32/WebRTC.framework/WebRTC -output out/WebRTC_arm


* suporot bitcode option
  ```
  $ python build_ios_libs.py --bitcode

