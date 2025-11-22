# Image Steganography – k-bit LSB Method

This project explores multiple image-steganography concepts, with the final implementation using the **k-bit Least Significant Bit (LSB)** method.

A simple LSB-based steganography tool is implemented that hides one image inside another and extracts it back without quality loss. The entire workflow is demonstrated in the Jupyter Notebook (`image processing.ipynb`), including embedding, generating the stego image, and recovering the hidden image with minimal visual distortion.

---

## Features
- Configurable **k-bit LSB** embedding  
- **Lossless extraction** of the hidden image  
- Very low distortion in the cover image  
- Step-by-step implementation in a single notebook  
- Clear separation of embedding and extraction functions  
- Supports standard image formats (PNG recommended)

---

## How It Works

### 1. Embedding
- Convert cover and hidden images into 8-bit pixel arrays.  
- Replace the **k least significant bits** of the cover image with the **k most significant bits** of the hidden image.  
- Save the result as the **stego image**.

### 2. Extraction
- Read the stego image.  
- Extract the **k LSBs** from each pixel.  
- Shift bits to reconstruct the original hidden image.  
- Output matches the original hidden image visually.

---

## Notebook Structure (`image processing.ipynb`)
The notebook includes:
- Loading and visualizing images  
- Bitwise encode/decode helpers  
- Embed function  
- Extract function  
- Reconstruction verification and pixel difference analysis  

---

## Requirements
pip install numpy opencv-python matplotlib

Usage
Embed
stego = embed_image(cover_img, secret_img, k=4)
cv2.imwrite("stego.png", stego)

Extract
recovered = extract_image(stego, k=4)
cv2.imwrite("recovered.png", recovered)

Limitations
Hidden image must fit within capacity of the cover image.
Use PNG or lossless formats; JPG compression damages LSB data.
```bash
