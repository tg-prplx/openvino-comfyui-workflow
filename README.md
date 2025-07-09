# Comfy UI OpenVINO

This ComfyUI workflow generates highly detailed anime-style summer beach scenes using advanced prompts and an upscaling model.  
**Tested on an Intel i7-6700HQ (integrated GPU): 2–3 seconds per iteration at 512x512 resolution.**

---

## 🚀 Overview

- **Purpose:** Generate anime images, such as multiple girls at the beach, with sunset lighting and cinematic style.
- **Positive prompt:** Focuses on masterpiece quality, expressive faces, dynamic composition, and rich detail.
- **Negative prompt:** Filters out common AI mistakes—extra limbs, poor anatomy, blur, duplicates, watermarks, etc.
- **Upscaling:** Uses a dedicated anime upscaler for higher-resolution results.
- **Ideal use:** Creating unique anime art, reference graphics, or project assets.

---

## 🧩 Requirements

- **ComfyUI** ([latest version](https://github.com/comfyanonymous/ComfyUI))
- **Models:**
  - Anime diffusion model (e.g., Counterfeit, Anything, AOM2, etc.)
  - Upscale model: `2x-AniScale.pth`
- **Hardware:** CUDA-compatible GPU recommended  
  - **CPU/Integrated GPU:** Works (slower). On Intel i7-6700HQ (integrated GPU), generation speed is ~2-3 s/it for 512x512 images.
- **Python >= 3.8**
- **Libraries:**  
  - torch >= 2.0  
  - torchvision  
  - numpy  
- Other ComfyUI dependencies (auto-installed with ComfyUI)

---

## 🛠️ Installation Guide

### 1. **Clone ComfyUI**

```bash
git clone https://github.com/comfyanonymous/ComfyUI.git
cd ComfyUI
```

### 2. **Install Python dependencies**

```bash
pip install -r requirements.txt
```
Make sure you have **Python 3.8 or higher** installed.

### 3. **Download models**
- Download your preferred **anime diffusion model** (Counterfeit, Anything-v3, AOM2, etc.) and place it into `models/Stable-diffusion/`.
- Download the upscaling model `2x-AniScale.pth` and place it into `models/upscale/`.

### 4. **(Optional) Install OpenVINO Node Support**
If you want to use OpenVINO acceleration:
```bash
# Instructions:
# https://github.com/openvino-dev-samples/comfyui_openvino
```

### 5. **Run ComfyUI**

```bash
# For CPU/integrated graphics
python main.py --cpu --use-pytorch-cross-attention --fast --async-offload --mmap-torch-files

# Or simple launch (will use available GPU if present)
python main.py
```

#### **Performance Note:**  
_On my Intel i7-6700HQ (integrated graphics), generation takes about 2–3 seconds per iteration for 512x512 images. On a modern GPU, generation can be almost instant._

---

## 📝 Prompt Examples

**Positive prompt:**
```
masterpiece, best quality, multiple girls, 1 girl, summer beach scene, sunset lighting, anime style, ultra detailed, dynamic composition, soft lighting, glowing water, perfect anatomy, expressive faces, different outfits, hair blowing in the wind, smiling, posing together, cinematic framing, golden hour, high detail background, wet skin, water reflections, beautiful sky, sunset clouds
```

**Negative prompt:**
```
worst quality, low quality, blurry, extra limbs, extra fingers, bad anatomy, duplicate faces, poorly drawn face, text, watermark, signature, cropped, nsfw, fused body, disfigured, long neck, cloned limbs, deformed eyes, long torso
```

---

## 🖼 Workflow Steps

1.  Install OpenVINO Node if you want hardware acceleration.
2.  Feed your prompts into **CLIPTextEncode** (positive/negative).
3.  Run the image generation with your chosen anime diffusion model.
4.  Apply upscaling via `2x-AniScale.pth` for high-res results.
5.  Save your finished images from the output folder.

---

## 📂 Usage

- Set up ComfyUI as above.
- Import or recreate the workflow via `.json` file or by configuring the nodes in ComfyUI manually.
- Start generating images with your prompts!

---

## ❗️ Notes

- If results look odd, experiment with prompts or sampling parameters.
- For best upscaling, use the latest compatible upscaler model.
- CPU & integrated GPU performance will be much lower vs. a dedicated NVIDIA GPU.

---

## 🔗 Useful Links

- [ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- [Anime models (CivitAI, HuggingFace, etc.)](https://civitai.com/)
- [ComfyUI Discord Community](https://discord.gg/comfyui)
- [OpenVINO ComfyUI Node](https://github.com/openvino-dev-samples/comfyui_openvino)

_Other dependencies are handled via ComfyUI’s setup._
