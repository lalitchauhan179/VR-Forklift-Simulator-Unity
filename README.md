# 🚜 Forklift VR Training Simulation

A VR + Desktop-compatible forklift training simulation built in **Unity 2022.3.21f1 (LTS)**, designed to teach safe forklift operation through immersive step-by-step instruction.

---

## 🛠️ Setup & Running the Project

### 📦 Prerequisites
- Unity Version: `2022.3.21f1 (LTS)`
- XR Plugin Management: Enabled in Project Settings

### 🖥️ Supported Platforms
- **VR Headset:** Oculus / SteamVR compatible
- **Desktop:** Keyboard and mouse

### 🔌 Dependencies (via Unity Package Manager)
- `XR Interaction Toolkit` (v2.3.2+)
- `Input System` (Active Input Handling must be set to "Both" or "Input System Package (New)")
- `TextMeshPro`
- `XR Plugin Management` (Oculus / OpenXR providers)

---

## 📁 Project Structure

 Assets/ ├── Scripts/ │ ├── ForkliftController.cs │ ├── ForkliftTrainingManager.cs │ ├── IgnitionButton.cs │ ├── TrainingLogger.cs │ └── VRInstructionUI.cs ├── Prefabs/ ├── Materials/ ├── UI/ ├── Scenes/ │ └── ForkliftTraining.unity

 
---

## ⚙️ Setting Up the Project

1. **Clone or Download** the project into your Unity Projects folder.
2. Open Unity Hub → **Click Add** → Select the project folder.
3. Open the scene: `Assets/Scenes/ForkliftTraining.unity`
4. **Enable XR Plugin:**
   - `Edit → Project Settings → XR Plugin Management`
   - Enable **Oculus** or **OpenXR** under the appropriate platform (Windows/Android).
5. **Set Input System:**
   - `Edit → Project Settings → Player → Other Settings`
   - Set "Active Input Handling" to `Both` or `Input System Package (New)`

---

## 🏁 Running the Simulation

### 🎮 VR Mode:
1. Connect your VR headset (Oculus/SteamVR).
2. Press **Play** in Unity Editor or build via `File → Build Settings`.
3. Interact using VR controllers: grab knobs, press dashboard buttons, operate the lift.

### 🖥️ Desktop Mode:
1. Press **Play** in Unity Editor.
2. Use the following keyboard controls:
   - `I` – Ignition  
   - `W/A/S/D` – Move & steer  
   - `Q / E` – Raise / Lower forks

---

## 🧪 Testing the Simulation

- Follow instructions shown in the in-cabin world-space UI.
- TrainingLogger.cs will automatically capture:
  - ⏱️ Task completion times
  - ✅ Completed objectives
  - ❌ Collisions or invalid actions

### 🗃️ Output Logs
- Logs are written by `TrainingLogger.cs` to:



---

## 📄 Developer Documentation

### 🎯 Design Goals

**Target Audience:**
- Warehouse workers, forklift trainees, VR training testers

**Learning Objectives:**
- Ignition/startup
- Driving and maneuvering
- Lifting/placing loads on target zones
- Safety and procedural awareness

**Methodology:**
- World-space UI (`VRInstructionUI.cs`)
- Task flow control via `ForkliftTrainingManager.cs`
- VR + Desktop support using device detection

---

## 🧠 Technical Highlights

**Input Handling:**
- VR: XR controllers with hand colliders
- Desktop: Keyboard input (fallback logic)

**Physics Simulation:**
- Rigidbody movement with torque and drag
- Fork lift via transform adjustments

**Key Scripts:**
- `ForkliftController.cs` – movement & physics
- `IgnitionButton.cs` – ignition interaction (VR, key, UI)
- `TrainingLogger.cs` – task logs & error tracking
- `VRInstructionUI.cs` – step-by-step guidance
- `ForkliftTrainingManager.cs` – task progression logic

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|----------|----------|
| Forklift physics realism | Used Rigidbody + torque (wheel colliders skipped for simplicity) |
| Cross-platform input | XRSettings.isDeviceActive → conditional input logic |
| Task guidance | Modular step controller with validation checks |
| User logging | TrainingLogger captures actions, collisions, time |
| Multi-mode ignition | Supported via collider, keyboard, and UI button |

---

## ✅ Implemented Features

- ✅ Interactive dashboard with TextMeshPro
- ✅ Unified training logic
- ✅ Logs output to text
- ✅ XR and desktop input fallback
- ✅ Scene structured and cleanly organized

---

## 💡 Future Enhancements

- 🧱 **Expanded scenarios**: stack pallets, tighter turns
- 🚧 **Advanced physics**: add wheel colliders
- 🔊 **Audio-visual feedback**: sounds, effects, UI polish
- 📊 **Scoring & analytics**: performance breakdowns
- 🚶 **Hazard simulation**: pedestrians, emergency stop
- 🌍 **Multilingual support**: Hindi, Japanese, etc.
- 🧩 **Modular training**: ScriptableObject-based training modules

---

**👋 Built by Lalit Kumar Chauhan**  
🔗 [LinkedIn](https://www.linkedin.com/in/lalit-chauhan179) | 📬 `lk149466@gmail.com`

---

