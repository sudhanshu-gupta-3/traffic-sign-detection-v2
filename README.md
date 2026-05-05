# Traffic Sign Detection (YOLOv8 + Streamlit UI)

A practical traffic-sign detection project with modern UI, training scripts, data augmentation, and deployment-ready setup.

## New capabilities
- ✅ **Live webcam detection** mode in UI.
- ✅ **Expanded class template** in dataset config.
- ✅ **Stronger training augmentations** exposed as CLI flags.
- ✅ **Premium UI** with dark mode and glassmorphism.

## Quick demo (local)
```bash
python -m venv .venv
# Activate venv:
# .venv\Scripts\activate (Windows) or source .venv/bin/activate (Linux/macOS)

pip install -r requirements.txt
python scripts/download_sample_model.py
streamlit run app.py
```

Open `http://localhost:8501` and choose **Image**, **Video**, or **Live Webcam**.

## Train for higher accuracy (with augmentation)
```bash
python scripts/train.py \
  --data data/traffic_signs.yaml \
  --model yolov8m.pt \
  --epochs 100 \
  --imgsz 960 \
  --batch 16 \
  --mosaic 1.0 \
  --mixup 0.1 \
  --degrees 8 --translate 0.1 --scale 0.5 --fliplr 0.5
```

## Evaluate
```bash
python scripts/evaluate.py --weights runs/detect/traffic_sign_train/weights/best.pt --data data/traffic_signs.yaml
```

## Deploy
### Docker
```bash
docker build -t traffic-sign-app .
docker run -p 8501:8501 traffic-sign-app
```
