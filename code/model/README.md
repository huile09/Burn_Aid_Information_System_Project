# 🧠 BurnAid AI - Pretrained Model Weights

### 📥 Download Pretrained Weights:
👉 **[Download ConvNeXtV2 & U-Net++ Models from Google Drive](https://drive.google.com/drive/folders/16Eioi25kgdv-j4CtXtLZ77SiB1kiOxuI?usp=sharing)**

*(After downloading, place both files into this models/ directory before launching the app).*

---

This directory manages the trained deep learning model checkpoints for the BurnAid AI system:

1. **convnextv2_burn_4class_best.pth (~57.2 MB)**
   - **Architecture:** ConvNeXtV2-Nano (	imm.create_model('convnextv2_nano.fcmae_ft_in22k_in1k', num_classes=4)).
   - **Task:** 4-class burn depth classification: *Degree I*, *Degree II*, *Degree III*, *No Burn*.
   - **Input:** 224 x 224 RGB, ImageNet normalized.

2. **est_random_curriculum_seed2026.pt (~99.7 MB)**
   - **Architecture:** UNetPlusPlus with ResNet-34 encoder (segmentation_models_pytorch).
   - **Training Strategy:** Curriculum Learning (Seed 2026) optimizing Dice Loss & BCE.
   - **Task:** Binary wound boundary segmentation and TBSA area quantification.
   - **Input:** 384 x 384 RGB.

---

### 📌 Note on Model Hosting & GitHub Web Uploads:
- The standard GitHub Web interface enforces a strict **25 MB/file** limit. Because these model weights exceed 25 MB, they are hosted on Google Drive for fast and reliable downloads.
- **Alternative distribution methods:**
  1. **GitHub Releases:** Upload the model binaries to a GitHub Release tag (1.0.0), which supports files up to **2 GB**.
  2. **Git LFS:** Track weights via .gitattributes when pushing through Git CLI or GitHub Desktop.
