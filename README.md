# Yoga Pose Live Detection

Real-time yoga pose classification in the browser. The model runs client-side with TensorFlow.js — the webcam feed never leaves the machine.

## What's in it

| Path | Role |
|---|---|
| `index.html` | The live detection page |
| `learn.js` | Loads the model and runs inference on the webcam stream |
| `modelCreation/dataCollection.js` | Captures training samples from the webcam |
| `modelCreation/modelTraining.js` | Trains the classifier in-browser |
| `modelCreation/modelDeploy.js`, `modelDeploy2.js` | Exports the trained model |
| `modelv2/model2.json` + `model.weights2.bin` | The trained model, committed and ready to load |

The whole loop — collect, train, deploy, run — happens in the browser, so there is no Python step anywhere.

## Tech stack

- **TensorFlow.js** for training and inference
- Webcam capture via `getUserMedia`
- Plain HTML, CSS and JavaScript

## Running it

The page loads model files over `fetch`, so opening `index.html` directly will fail on CORS. Serve the folder instead:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`. Allow camera access when prompted.

Any static server works, for example:

```bash
npx serve
```

## Training your own

1. Open the data collection page and record samples for each pose
2. Run training — it happens live in the browser
3. Export, and drop the output into `modelv2/`

## Known gaps

- Accuracy depends heavily on lighting and camera angle.
- The pose set is fixed to whatever the committed model was trained on.

## License

See `LICENSE` in this repository.
