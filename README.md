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
<img width="1174" alt="image" src="https://github.com/user-attachments/assets/ac919047-6ebe-412b-94a4-f7f2abad4be1" />


5. In the last code cell, run this command:
   ```bash
   !streamlit run app.py &>/content/logs.txt & npx localtunnel --port 8501 & curl ipv4.icanhazip.com

Click this URL to access your Streamlit app.

<img width="1174" alt="image" src="https://github.com/user-attachments/assets/de60af71-b43a-4eca-8856-87c6ad037f77" />

6. When prompted, paste the Tunnel Password from step 5.

<img width="1174" alt="image" src="https://github.com/user-attachments/assets/c0ac1f23-ac90-4171-8439-c4f0c32ded04" />

7. Once authenticated, the web app will open and you’ll see the interactive interface like below:
<img width="1174" alt="image" src="https://github.com/user-attachments/assets/4999ff37-4ad6-4eb5-a2b6-498b747d3547" />

8. To get started, please see the example workflow or watch the video tutorial provided below.
---

## 🖼 Example Workflow

1. Upload an H&E or DAB-stained image   
<img width="553" alt="image" src="https://github.com/user-attachments/assets/d4372490-ac88-4ad3-ba42-0a11315c5af6" />

2. Click the Preview H and D channels get color deconvolution
<img width="575" alt="image" src="https://github.com/user-attachments/assets/a876f3f2-9acf-4897-9cea-78b38ff55a97" />

3. 💡 If the preview result is not satisfactory, adjust the percentile-based contrast ranges
      and then re-click the **Preview H and D channels** button to update the visualization.
<img width="571" alt="image" src="https://github.com/user-attachments/assets/3d307e25-6086-4dab-8b30-760a723465fd" />

4. Run Cellpose segmentation
<img width="561" alt="image" src="https://github.com/user-attachments/assets/511f1511-cb5f-4e47-ae05-3e65bab6a6fd" />

5. Automatically compute:
   - Total cells (from H channel)
   - Ki67-positive cells (from D channel)
   - Proliferation index (%) = D / H × 100
<img width="562" alt="image" src="https://github.com/user-attachments/assets/607ee609-2a26-457d-b6af-0d59afdc4ce9" />

---

## 🎥 Watch Video Tutorial

[![Watch the tutorial on YouTube](https://img.youtube.com/vi/aI19rF6wwPc/0.jpg)](https://youtu.be/aI19rF6wwPc?si=3N8ps4uLSC8Yg3-7)

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


