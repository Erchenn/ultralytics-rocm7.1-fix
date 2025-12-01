Just put ultralytics.py in extensions/adetailer/adetailer

Ultralytics 8.2–8.3 introduced a regression where custom YOLO .pt models
(C3k, C3TR, Focus, SPPF, Res) fail to load properly.
As a result, ADetailer receives empty masks (None), causing inpainting not to work.

This patch restores backward compatibility by reintroducing missing layer classes
and correcting class resolution during model deserialization.

Tested with:
- Radeon RX 9070XT
- ROCm 7.1.1
- Pytorch 2.7.1+rocm7.1.1
- ADetailer 25.3.0
- Stable Diffusion XL
