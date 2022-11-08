XR Privacy Framework
=========
# Who this framework is for?

The XR Privacy Framework (or "XRPF") is for **App Developers** to give their participants control of their data and privacy while collecting additional insights from their applications. It is also for **Tool Developers** that want to build a transparent privacy standard through the XR ecosystem.

# Contributions

- Proposals for including additional hardware and software
- CC0 Iconography
- Typos or edits for clarity (grammar, descriptions, use cases)

# Concepts and Terminology

- **XR** - any augmented reality, virtual reality or mixed reality experience
- **Data Sources** - a grouping of data that is reasonably connected to provide a high level agreement about what the user finds acceptable to collect. This may refer to both a technical grouping (eg, GPU, CPU and OS are all device-specific elements) or a conceptual level (eg, fixations and heart rate aren’t directly related, but the source is the user’s body)

# What is this framework?

XRPF is not a privacy policy and is not legally binding - it is a framework to inform participants about data the app is recording. An App Developer and Tools Developer should have a privacy policy to specify how data is collected and used in greater detail available in their application and/or website, and disclose any applicable subprocessors. 

XRPF is an framework that defines consent between the App Developer and the participant about the types of data being recorded, falling into 5 categories:

- Hardware Data
- Spatial Data
- Location Data
- Biometric Data
- Social Data

What can the App Developer do with the data after recorded?

- The App Developer is free to use the data as they see fit (for research, training, app optimization, app monetization, etc). These uses should be indicated in their privacy policy.

As XRPF is a specification beyond the scope of a single piece of software, implementations will change as technology changes. This specification will be updated with the following goals:

- Give participants a reasonable understanding about the data they make available
- Allow developers to gain additional value from the data their participants have agreed to provide

# Why do we need this?

Many data sources are outside the available permissions agreement popups on Android devices or PCs. These sources can be important for building XR experiences:

- Location data - app will already ask for permission
- Social data - app will already ask for permission
- Hardware data - not asked for permission
- Spatial data - not asked for permission
- Biometric data - not asked for permission (depends on the device)

Additionally, we believe participants should be able to have feature rich XR experiences (powered by these data sources) without compromising their privacy. Correct implementation of this privacy framework separates data used by the app to deliver these experiences and data available to the developer.

# Implementing the Framework

- See [Unity Implementation](https://github.com/CognitiveVR/xrprivacyframework-unity) and [Unreal Implementation](https://github.com/CognitiveVR/xrprivacyframework-unreal) for more concrete examples
- The developer should provide non-technical descriptions of features for participants
- The developer should customize the description of biometric data sources (if used)
- The developer should not disable app features if certain data sources are not selected, just the recording of that data
- The developer should display the agreement before data is recorded
- The developer should allow a user to change their agreement from a reasonably accessible menu option later
- The developer should include a link to their privacy policy for further information

## Allowances

- This agreement may be waived if you receive informed consent by the user in another method, such as written consent in an academic study or via an employment agreement in the case of learning and development. Consider including a popup in XR informing your user that data is being recorded regardless
- Customize UI visuals and controls for your application
- Remove data sources agreements for invalid options (eg, the Oculus Quest doesn’t include any biometric sensors, so this option doesn’t need to be displayed)
- You may **require** the user to agree with the hardware data source to continue using your app. This should not include any personally identifying information
- You may save the agreement for a participant - this agreement does not need to be accepted each session

# Supporting the Framework

When a participant is presented with the agreement, their choice should set certain flags in the application. Recording data should respect the flags set by the user’s choices.

**Tools Developers** (such as analytics, advertisement or machine learning companies) should build their SDKs to enable or disable collection of data respecting these flags.

**App Developers** should ensure that the tools they are using correctly implement this standard.


# Data Source Reference

This lists all kinds of data available to the app that is potentially sensitive and should be disclosed to the user when collected. Some include kinds of data recorded (eg, room size accuracy) have restrictions that should be included as well.

This section indicates certain types of data that should never be recorded, even if they are available to the application.

## Hardware Data

This covers any hardware used for the experience.

- **NO INDIVIDUAL HARDWARE SERIAL NUMBERS**
- **NO MAC ADDRESS**
- **NO IMAGES FROM PASS THROUGH CAMERA**
- Device id implementation - combination of serial numbers. To track device over multiple sessions
- IP address (agreement of this data source might identify country and city)
- Friendly name of HMD (eg, Pico Neo 3 Eye)
- CPU manufacturer and type (eg Intel i7-1200)
- GPU manufacturer and type (eg NVIDIA RTX 2060)
- OS version (eg Windows 11 Rev 2)
- Battery level of HMD and controllers
- Date/time when app was launched
- Framerate over time
- Dropped frames over time
- Performance data (eg, gpu time per frame, memory usage, etc)

## Spatial Data

This covers HMD and controller movement in VR space and the VR space itself

- Positions of events in XR space
- Position and rotation of HMD in XR space (can infer height)
- Position and rotation of controllers in XR space (can infer arm length)
- Position and rotation of additional tracking devices (such as Vive Trackers)
- Room size (to rectangular area and 10cm accuracy)
- Direction of gaze (including eye direction if hardware is available) at a fixed interval
- Surface sizes and positions detected in AR

## Location Data

This covers location data primarily for outdoor augmented reality experiences

- Latitude, longitude and elevation
- Compass direction

## Social Data

This covers non-identifiable multiplayer gameplay and social engagements

- **NO REAL NAMES OR USERNAMES OF USER OR FRIENDS**
- Number of friends in room/group/app
- User’s organization scoped id
- Number of friends on the friends list
- Number of friends in the room
- Number of recently met users

## Biometric Data

This covers sensors that record biometric data

- **NO IMAGES OF USER'S EYES**
- Fixations and saccades using eye tracking hardware
- Cognitive load (from HP Omnicept)
- Heartrate
- Heartrate variance
- Electromyography (emg)
- Electroencephalography (eeg)
- Electrocardiogram (ecg or ekg))
- Galvanic Skin Response (gsr)
- High fidelity motion tracking (eg Teslasuit)
