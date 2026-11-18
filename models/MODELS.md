# Bundled ML models (same-origin, never fetched from the internet at runtime)

| File | Used by | Source URL (downloaded once at build setup) | sha256 | Bytes | Licence |
|---|---|---|---|---|---|
| `blaze_face_short_range.tflite` | Face blur on clip export (FR-SHARE-05, SPEC §0.2 item 6) via MediaPipe Face Detector (`@mediapipe/tasks-vision` 0.10.32) | https://storage.googleapis.com/mediapipe-models/face_detector/blaze_face_short_range/float16/1/blaze_face_short_range.tflite | `b4578f35940bf5a1a655214a1cce5cab13eba73c1297cd78e1a04c2380b0152f` | 229746 | Apache-2.0 (MediaPipe model card: BlazeFace short range) |

Related, not in this folder: `../spike-models/pose_landmarker_lite.task` (Pose Landmarker lite, Apache-2.0) is used by
the Phase 0 spike and by Lab mode (D23). The MediaPipe wasm files in `../spike-models/` are copied from
`node_modules/@mediapipe/tasks-vision/wasm` at build time (vite.config.ts), pinned 0.10.32 (QA-07: 1.x adds telemetry).

Caching: these files are excluded from the service-worker precache (vite.config.ts `globIgnores`). The service worker
caches them on first use (runtime cache `allezo-ml`), and switching on Lab mode downloads them into that cache up front.

Verify: `sha256sum web/public/models/blaze_face_short_range.tflite`.
