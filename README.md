# Ki67_positive_cell_counter
This interactive web app allows users to upload histopathological images (e.g., IHC-stained tissues) and count Ki67-positive cells versus total cells using deep-learning-based segmentation via [Cellpose](https://www.cellpose.org/). It is designed to work seamlessly in Google Colab using `streamlit` and `localtunnel`.


## 🚀 Launch in Google Colab

You can run this app entirely in the cloud using Google Colab.  
Please follow the instructions **step-by-step** to ensure **GPU** support and successful tunnel setup.

### ✅ Step-by-step Instructions

1. **Click the button below to open the Colab notebook:**

   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1xXbcXlTgoMBjKhtkVYsz0DMwsaF90iWK?usp=sharing)


2. **Change the runtime type to use a GPU**:  
   - At the top of the Colab window, go to:  
     `Runtime` → `Change runtime type`  
   - Set **Hardware accelerator** to **GPU** (e.g. A100 GPU, T4 GPU) 
   - Click **Save**

3. **Run all cells one by one**

4. In the **second-to-last code cell**, you will see:

   ```bash
   !wget -q -O - https://loca.lt/mytunnelpassword


This will display a Tunnel Password. Copy and keep this password — you’ll need it in the next step.

5. In the last code cell, run this command:
   ```bash
   !streamlit run app.py &>/content/logs.txt & npx localtunnel --port 8501 & curl ipv4.icanhazip.com

Click this URL to access your Streamlit app.

6. When prompted, paste the Tunnel Password from step 5.
Once authenticated, the web app will open and you’ll see the interactive interface like below:
<img width="1174" alt="image" src="https://github.com/user-attachments/assets/c0ac1f23-ac90-4171-8439-c4f0c32ded04" />

## 🖼 Example Workflow

1. Upload an H&E or DAB-stained image
2. Preview Hematoxylin (H) and DAB (D) channels via color deconvolution
3. Adjust percentile-based contrast range
4. Run Cellpose segmentation
5. Automatically compute:
   - Total cells (from H channel)
   - Ki67-positive cells (from D channel)
   - Proliferation index (%) = D / H × 100

---

## 📸 Preview

| Upload | H & D Channels | Output with Overlays |
|--------|----------------|-----------------------|
| ![Upload](images/upload.png) | ![Channels](images/hed_preview.png) | ![Overlay](images/overlay_result.png) |

> *(Replace these with your own screenshots if available)*

---

## 🔧 Features

- ✅ Streamlit-based user interface
- ✅ HED color deconvolution (skimage)
- ✅ Cellpose model (`cyto`) integration
- ✅ GPU support (if available in Colab)
- ✅ Ratio calculation: Ki67+ / Total cells
- ✅ Side-by-side visualization and downloadable summary

---

## 📦 Dependencies

Install via pip (automatically handled in Colab):

```bash
opencv-python-headless<4.3
cellpose
streamlit
pyngrok
numpy==1.23.5
matplotlib
scikit-image


