# Gaze contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Gaze**
- Repo: `computerpets-gaze`
- Category: AI & GPU
- Idea: Vision React App
- Port / surface: `5173`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Gesture(kind, confidence, bbox) · Calibration(cameraId, restPose) · PrivacyMode(local|opt-in-cloud)

## Surface

- WS /v1/gestures — stream {kind: wave|point|present|absent, confidence, ts}
- POST /v1/calibrate — capture a 5-second rest pose for this camera
- GET /v1/privacy — camera is local-first; frames never leave the box unless opted in

## Neighbors

- computerpets desktop overlay (gesture events)
- computerpets-cortex (narrate what it saw)
- computerpets-motion (trigger animations)

## Failure doctrine

No camera → pets ignore vision, never crash. Low light → 'absent' not 'dead'. Permission denied → one tray balloon, then quiet.

## Stack

TypeScript · React 19 · Vite · MediaPipe / TensorFlow.js · WebRTC getUserMedia · optional ONNX GPU runtime
