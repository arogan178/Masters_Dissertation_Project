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

## Running it

1. Install Unity **2022.2.0f1** through Unity Hub, with Android build support.
2. Clone the repo and add the folder as a project in Unity Hub.
3. Get a HypeRate API token from <https://www.hyperate.io/api> and set it in the `websocketToken` field of the heart-rate component in the Inspector. Don't commit it.
4. Open `Assets/Scenes/Menu.unity` and press Play, or build for Android.

## License

My own source code (the C# scripts outside third-party folders) is [MIT](LICENSE) licensed. Third-party assets and plugins keep their own licenses. That includes the HypeRate SDK, the Unity Asset Store packs (AurynSky, Nomads Music, Score and Times, Spags Assets), TextMesh Pro, and the bundled DLLs under `Assets/Plugins`.
