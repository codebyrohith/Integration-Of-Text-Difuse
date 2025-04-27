# Integration-Of-Text-Difuse

## Overview

This project provides a Flask-based API to fuse two images — a product image and a texture/logo image — using the Text-DiFuse diffusion model (NeurIPS 2024).  
It enables creative fusion like applying artistic textures or seamless branding on products.

## Setup Instructions

- **Python Version:** Python 3.8 or higher

- **Install Dependencies:**

```bash
pip install flask torch torchvision opencv-python
```

- **Place Model Checkpoints:**

  - `diffusion_stage1.pth`
  - `diffusion_stage2.pth`
  - `FCM-VIS-IR.pt`

- **Run the Flask Server:**

```bash
python app.py
```

(Optional) Use Cloudflare Tunnel to expose the server publicly.

## API Usage

- **Endpoint:** `/api/fuse`
- **Method:** `POST`
- **Parameters:**
  - `vis`: Product Image (file upload)
  - `ir`: Texture or Logo Image (file upload)

### Example cURL Command

```bash
curl -X POST http://127.0.0.1:5000/api/fuse \
     -F "vis=@path/to/product.png" \
     -F "ir=@path/to/texture.png" \
     --output fused_output.png
```

## Screenshots

| Description                 | Screenshot          |
| :-------------------------- | :------------------ |
| 1. Input Product Image      | _images/input1.png_ |
| 2. Input Texture/Logo Image | _images/input2.png_ |
| 3. Fused Output Image       | _images/output.png_ |
| 4. API Test Result          | _images/api.png_    |

## Limitations

- Not suitable for exact cut-and-paste compositing.
- Works best when input images have similar style/modality.
- GPU recommended for faster fusion; CPU will be slow.
- Limited fine control over fusion areas.

## Credits

- **Model:** [Text-DiFuse - NeurIPS 2024](https://proceedings.neurips.cc/paper_files/paper/2024/hash/45e409b46bebd648e9041a628a1a9964-Abstract-Conference.html)
- **Team Members:** Rohith, Vinay Joshva, Hrishikesh Komaragiri, Sunil Reddy Janapala
