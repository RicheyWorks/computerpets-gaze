# Gaze

**Vision React App** — Webcam computer vision so desktop pets react to physical gestures in the room.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

Pets already walk on the real desktop. Gaze lets them see you: wave, sit still, hold up a treat, leave the chair. The overlay stays a living sticker — this is the eyes.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Gaze does not replace that. It is one organ.

## Stack

TypeScript · React 19 · Vite · MediaPipe / TensorFlow.js · WebRTC getUserMedia · optional ONNX GPU runtime

GroupId / namespace: `com.enterprisepet.gaze`  
Default listen: `5173`

## Talks to

- computerpets desktop overlay (gesture events)
- computerpets-cortex (narrate what it saw)
- computerpets-motion (trigger animations)

## Contract

### Data

`Gesture(kind, confidence, bbox) · Calibration(cameraId, restPose) · PrivacyMode(local|opt-in-cloud)`

### Surface

- WS /v1/gestures — stream {kind: wave|point|present|absent, confidence, ts}
- POST /v1/calibrate — capture a 5-second rest pose for this camera
- GET /v1/privacy — camera is local-first; frames never leave the box unless opted in

### Failure doctrine

No camera → pets ignore vision, never crash. Low light → 'absent' not 'dead'. Permission denied → one tray balloon, then quiet.

## Layout

```
computerpets-gaze/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
cd app; npm install; npm run dev
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-gaze](https://github.com/RicheyWorks/computerpets-gaze) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
