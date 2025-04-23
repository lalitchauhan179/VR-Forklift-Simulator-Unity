🛠️ Setup & Running the Project
📦 Prerequisites
• Unity Version: Ensure Unity 2022.3.21f1 (LTS) is installed.
• XR Plugin Management: Enabled in Project Settings
• Supported Platforms:
o VR Headset: Oculus or SteamVR compatible
o Desktop: Keyboard and mouse
🔌 Dependencies
Make sure the following packages are installed via Unity Package Manager:
• XR Interaction Toolkit (v2.3.2 or newer)
• Input System (new Input System must be enabled)
• TextMeshPro
• XR Plugin Management (Oculus/SteamVR providers)
📁 Project Structure
CopyEdit
Assets/
├── Scripts/
│ ├── ForkliftController.cs
│ ├── ForkliftTrainingManager.cs
│ ├── IgnitionButton.cs
│ ├── TrainingLogger.cs
│ └── VRInstructionUI.cs
├── Prefabs/
├── Materials/
├── UI/
├── Scenes/
│ └── ForkliftTraining.unity
⚙️ Setting Up the Project
1. Clone or Download the project into your Unity projects folder.
2. Open Unity Hub → Click Add → Select the project folder.
3. Open the Scene: Navigate to Assets/Scenes/ForkliftTraining.unity and open it.
4. Check XR Setup:
o Go to Edit → Project Settings → XR Plugin Management
o Enable Oculus or OpenXR under the appropriate platform (Windows, Android, etc.)
5. Set Active Input System:
o Go to Edit → Project Settings → Player → Other Settings
o Make sure Active Input Handling is set to Both or Input System Package (New)
🏁 Running the Simulation
In VR Mode:
1. Connect and turn on your VR headset.
2. Press Play in Unity Editor or build the project using File → Build Settings.
3. Interact using VR controllers (grab knob, press buttons, use lift lever).
In Desktop Mode:
1. Press Play in the Unity Editor.
2. Use keyboard controls:
o I – Ignition
o W/A/S/D – Move forward/back and steer
o Q / E – Raise / Lower the forks
🧪 Testing
• Ensure you follow all the training steps as guided by the in-cabin instruction UI.
• Data logging will auto-capture:
o Timestamps
o Task completions
o Collisions or invalid interactions
🗃️ Logs & Output
• Logs are written by TrainingLogger.cs into a text file.
• You can configure the output location in the script (default is inside the project under Assets/Logs/).


📄 Forklift VR Training Simulation — Developer Documentation
🔧 Unity Version
• Unity 2022.3.21f1 (LTS)
🎯 Initial Design Considerations
Target Audience:
• Individuals training for forklift certification
• Factory and warehouse workers transitioning to machinery operation
Learning Objectives:
• Teach ignition and startup procedure via interactive 3D button or VR trigger.
• Train users to operate steering, acceleration, and braking using natural motion controls or keyboard equivalents.
• Demonstrate safe lifting and load placement of a cardboard box onto a designated red-marked area.
Training Methodology:
• Visual feedback and instruction via a world-space UI (VRInstructionUI.cs)
• Step-by-step task progression managed through ForkliftTrainingManager.cs
• Both VR and desktop support to make the training accessible to a wider audience
🧪 Technical Approach
VR SDK & Input:
• Unity XR Interaction Toolkit
• Compatible with Oculus and SteamVR
Input Method Implementation:
• VR: Uses hand colliders or XR input buttons to interact with dashboard buttons (e.g., ignition).
• Desktop: Keyboard input fallback: I for ignition, WASD for movement, Q/E for lifting.
Physics Simulation:
• Forklift motion via Rigidbody, torque-based rotation, capped velocity.
• Forklift forks raised/lowered using custom lift script bound to input.
Key Scripts:
• ForkliftController.cs: Manages movement and physics.
• IgnitionButton.cs: Allows ignition via collision, key press, or UI button click.
• TrainingLogger.cs: Logs user actions, errors, and completion time.
• VRInstructionUI.cs: Displays in-cabin instruction text.
• ForkliftTrainingManager.cs: Manages step logic and instruction flow.
🚧 Challenges Faced
1. Forklift Movement Simulation
• Challenge: Achieve realistic motion without full-blown wheel colliders.
• Solution: Torque-based movement, speed caps, Rigidbody drag balancing.
2. Cross-Platform Input Compatibility
• Challenge: Differentiating input for VR vs desktop.
• Solution: Used XRSettings.isDeviceActive to determine input mode and switch listeners accordingly.
3. Clear In-Game Instruction Flow
• Challenge: Ensuring users follow training steps in order.
• Solution: ForkliftTrainingManager.cs checks for task completion before advancing instruction.
4. User Error Detection & Logging
• Challenge: Log collisions and incorrect task attempts.
• Solution: TrainingLogger.cs logs collisions via Unity's OnCollisionEnter, tracks timestamps and task sequences.
5. Ignition System Control
• Challenge: Provide multiple ignition methods (VR, desktop, fallback UI).
• Solution: IgnitionButton.cs allows activation through:
o Hand/collider touch in VR
o Key I for desktop
o UI button press
✅ Solutions Implemented
• 3D instructional UI on dashboard using TextMeshPro
• Unified step controller (ForkliftTrainingManager.cs) for consistent guidance
• Scripted input-based interaction for lifting, steering, and ignition
• Scene-aware data logger (TrainingLogger.cs) that outputs to text
• UI fallback for ignition to improve accessibility
• Scene organization with folders: Scripts/, Prefabs/, UI/, Materials/
💡 Suggestions for Future Improvement
1. Expanded Scenarios
o Add additional objectives (e.g., stack pallets, navigate tight aisles)
2. Forklift Physics
o Replace simple Rigidbody control with Unity Wheel Colliders or custom physics joints
3. Audio-Visual Feedback
o Add sound effects: ignition, movement, collision, task completion
o Animations for buttons, fork movements
4. Training Analytics & Scoring
o Score based on completion time, errors, smoothness of movement
o Display performance breakdown at session end
5. Real-World Hazards Simulation
o Introduce obstacles, pedestrians, emergency scenarios
6. Accessibility & Multi-language Support
o Instruction UI can support Hindi/Japanese/English toggles
7. Modular Instruction System
o Use ScriptableObject-based training modules for reusable instruction sets
