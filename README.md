# Pain Management and Conditioning through Virtual Reality and Affective Computing

Unity project for my MSc in Artificial Intelligence dissertation. It is a VR distraction-therapy game that reads a participant's heart rate from a smartwatch and uses machine learning to adapt the experience to their emotional state.

**Paper:** [IEEE Xplore](https://ieeexplore.ieee.org/document/10385256/) · [ResearchGate](https://www.researchgate.net/publication/376390002_Pain_Management_and_Conditioning_through_Virtual_Reality_and_Affective_Computing)

## Abstract

This study investigates the real-world efficacy of tailored pain management methods, focusing on Virtual Reality (VR) distraction therapy — a technique utilising immersive VR experiences to divert attention from pain. Participants undergo two phases consisting of VR therapy with simultaneous physiological data collection and the delivering of a conditioning stimulus via a smartwatch. Utilising machine learning, the VR experience is able to adapt to emotional states, ensuring that an individual's focus is shifted away from pain. Results reveal an overall 42% pain reduction, offering insights into diverse pain interventions.

## How it works

- **Heart rate:** streamed live from a smartwatch through the [HypeRate](https://www.hyperate.io/) WebSocket API.
- **Baseline:** a calibration phase records each participant's resting vitals (`BaseLineAcquisition.cs`).
- **Adaptation:** neural networks in `Assets/Scripts/ML` classify the participant's state and adjust the game. The folder includes backpropagation, particle swarm (PSO) and evolutionary (EO) trained variants.
- **Scenes:** an adaptive game (`AffectiveGame`), a randomised variant (`RandomGame`), plus device pairing, player selection and menus.
- **Target:** Android phones in a Google Cardboard headset (Cardboard XR plugin).

## Third-party assets not included

This repository contains my scripts, scenes and project settings only. The following third-party content was used in the study but can't be redistributed, so it has been removed:

| Asset | Folder it belongs in | Needed for |
| --- | --- | --- |
| ZenFulcrum *Tracks!* (ZF Track) | `Assets/ZFTrack` | **Required to compile.** Six scripts (`TrackSetup.cs`, `RandomTrackSetup.cs`, `TrackVisibility.cs`, `TrackVisibilitySwitch.cs`, `PlayerScript.cs`, `Switcher.cs`) use `ZenFulcrum.Track`. |
| Environment, animal and spaceship assets from the PhD project this work extends | `Assets/Graphics` | Scene visuals and ambient animal behaviour |
| AurynSky *Gems Ultimate Pack* | `Assets/AurynSky` | Gem visuals |
| Nomads Music *Soundspack 05 (8bit SFX 01 — Shooting Game) Lite* | `Assets/Nomads Music` | Sound effects |
| Game Sound Solutions *Score and Times* | `Assets/Score and Times - Game Sound Solutions` | Sound effects |
| Spags Assets crosshairs | `Assets/Spags Assets` | Crosshair textures |
| Sabresaurus *PlayerPrefs Editor & Utilities* | `Assets/PlayerPrefsEditor` | Editor-only tool, optional |
| HeatleyBros *8 Bit Adventure!* | `Assets/Music` | Background music |

Import the Unity Asset Store packs through the Package Manager (**My Assets**) into the folders above. Scenes will show missing references until they are restored.

## Running it

1. Install Unity **2022.2.0f1** through Unity Hub, with Android build support.
2. Clone the repo and add the folder as a project in Unity Hub.
3. Import the third-party assets listed above. At minimum, ZF Track is needed for the project to compile.
4. Get a HypeRate API token from <https://www.hyperate.io/api> and set it in the `websocketToken` field of the heart-rate component in the Inspector. Don't commit it.
5. Open `Assets/Scenes/Menu.unity` and press Play, or build for Android.

## Acknowledgements

This project extends the future-work direction of an earlier PhD project, whose environment and animal assets it used.

## License

My own source code is [MIT](LICENSE) licensed. It does not cover the removed assets above, or the bundled third-party code that remains: the HypeRate SDK, AsyncAwaitUtil, TextMesh Pro, the Google Cardboard and Mobile Notifications samples, and the DLLs under `Assets/Plugins`. Each keeps its own license.
