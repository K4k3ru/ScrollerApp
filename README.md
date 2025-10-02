# Bluetooth Earphone Scroller

An Android application that provides system-wide scrolling functionality using Bluetooth earphone buttons. The app can overlay other applications and inject scroll events based on earphone button presses.

## Features

- **System-wide scrolling**: Control scrolling in any app using Bluetooth earphone buttons
- **Overlay indicator**: Optional visual indicator showing when the service is active
- **Customizable button mapping**: Configure which earphone buttons perform which actions
- **Adjustable scroll settings**: Control scroll speed and distance
- **Accessibility service integration**: Uses Android's accessibility API for gesture injection
- **Foreground service**: Runs continuously in the background for reliable button detection

## Requirements

- Android 7.0 (API 24) or higher
- Bluetooth earphones with media control buttons
- System overlay permission
- Accessibility service permission
- Notification permission (Android 13+)

## Installation

1. Clone this repository
2. Open the project in Android Studio
3. Build and install the APK on your device
4. Grant the required permissions when prompted

## Setup Instructions

1. **Grant System Overlay Permission**:
   - Open the app and tap "Grant Permissions"
   - Enable "Display over other apps" permission

2. **Enable Accessibility Service**:
   - Tap "Open Accessibility Settings"
   - Find "Scroller Service" in the list
   - Enable the service

3. **Grant Notification Permission** (Android 13+):
   - Allow notifications when prompted

4. **Start the Service**:
   - Tap "Start Scroller Service"
   - The service will run in the background

## Usage

### Default Button Mapping
- **Volume Up**: Scroll up
- **Volume Down**: Scroll down  
- **Play/Pause**: Toggle overlay indicator

### Customization
- Open Settings to customize button mappings
- Adjust scroll speed and distance
- Configure overlay preferences

## Technical Details

### Architecture
- **MainActivity**: Main UI and permission handling
- **OverlayService**: Foreground service for overlay management
- **ScrollAccessibilityService**: Accessibility service for gesture injection
- **MediaButtonReceiver**: Broadcast receiver for Bluetooth button events
- **SettingsActivity**: Configuration interface

### Permissions Required
- `SYSTEM_ALERT_WINDOW`: For overlay functionality
- `BIND_ACCESSIBILITY_SERVICE`: For scroll gesture injection
- `BLUETOOTH_CONNECT`: For Bluetooth button detection
- `FOREGROUND_SERVICE`: For background operation
- `POST_NOTIFICATIONS`: For service notifications (Android 13+)

### How It Works
1. The app registers a broadcast receiver for media button events
2. When a Bluetooth earphone button is pressed, the receiver captures the event
3. Based on user configuration, the appropriate action is triggered
4. For scroll actions, a message is sent to the accessibility service
5. The accessibility service injects touch gestures to simulate scrolling

## Troubleshooting

### Service Not Responding
- Ensure all permissions are granted
- Restart the service from the main app
- Check that Bluetooth earphones are connected

### Scrolling Not Working
- Verify the accessibility service is enabled
- Some apps may not respond to injected gestures
- Try adjusting scroll speed and distance in settings

### Button Presses Not Detected
- Ensure Bluetooth earphones are properly connected
- Check that media controls work in other apps
- Some earphones may use different key codes

## Development

### Building from Source
```bash
git clone https://github.com/yourusername/bluetooth-scroller.git
cd bluetooth-scroller
./gradlew assembleDebug
```

### Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly on different devices
5. Submit a pull request

## Privacy

This app:
- Does not collect or transmit any personal data
- Only monitors media button presses when the service is active
- Uses accessibility permissions solely for scroll gesture injection
- All data stays on your device

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

This app uses accessibility services and system overlay permissions. While designed to be safe and privacy-focused, use at your own discretion. The developers are not responsible for any issues that may arise from using this application.