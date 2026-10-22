# CAD Editing — Yanxi Lin

[Live interactive demo](https://lyx-091610086.github.io/cad-editing-lab/)

A research reproduction and engineering integration portfolio for text-guided CAD editing with pretrained Microsoft CAD-Editor models.

## What you can explore

- Synchronized original and generated CAD views, with a separately labeled reference target.
- 9 selected end-to-end B-route examples; an optional diagnostic archive retains all 17 recorded cases and 51 calls.
- Predicted masks, decoded model outputs, reconstruction evidence, and STEP/STL downloads.
- English and Chinese interfaces, an attempt ledger, and a reproduction kit.

Route B uses the locating model's predicted mask before infilling. Route A uses a target-assisted reference mask for diagnosis. These purposefully selected training examples are a demonstration, not a held-out accuracy benchmark. The website replays recorded inference; it does not run models in the browser.

## Engineering scope

Compatible causal-LM inference runner, token-length output slicing, isolated prediction inputs, one-base adapter switching, OpenCascade reconstruction, and linked evidence for each result. The recorded local setup uses Llama 3 8B with NF4/BF16 on an RTX 5060 8 GB. No model training was performed for this portfolio.

## Source and deployment

The complete static website and validation script are packaged in `site-source.zip`. Extract the archive to edit `dist/index.html`, `dist/assets/`, and `scripts/check_static.py`.

GitHub Actions extracts that archive, validates its links and mesh indices, and publishes `dist/` to GitHub Pages. The workflow has read-only repository contents permission. Push an updated site-source.zip to main to publish a new version.

After extraction, run:

```bash
python3 scripts/check_static.py
node --check dist/assets/app.js
```

Serve dist/ over HTTP for local viewing. The interactive 3D viewer requires WebGL; raw evidence and CAD downloads remain accessible when WebGL is unavailable.

## Evidence and credits

Research reproduction and engineering integration by Yanxi Lin. Model architecture and pretrained checkpoints by the original CAD-Editor authors. This project uses Meta Llama 3, CAD-Editor, and third-party rendering tools; retained notices are in dist/assets/third-party-notices.txt inside the archive.

- [CAD-Editor paper](https://arxiv.org/abs/2502.03997)
- [Official CAD-Editor implementation](https://github.com/microsoft/CAD-Editor)
- [Original hosted portfolio](https://cad-editing-lab.free-harp-2721.chatgpt.site)
