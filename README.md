# Synthetic Face Generation for Creative Automation

This project is a full-stack web application that leverages state-of-the-art generative models to create and semantically edit photorealistic synthetic faces. It addresses the challenge of creating high-quality, customizable human images, which is often expensive, time-consuming, and limited by privacy concerns.

The application provides a powerful and flexible solution by pairing a **StyleGAN2-ADA** generator with a **HyperStyle** encoder for image inversion and **GANSpace** for detailed semantic editing.

## Core Features

  * **High-Fidelity Face Inversion:** Convert any uploaded portrait photo into a manipulable latent vector using the HyperStyle encoder.
  * **Detailed Attribute Customization:** Fine-tune dozens of facial attributes in real-time, including age, gender, smile, lighting, eye color, and more.
  * **Marketing & Advertising Automation:** An automated pipeline to generate virtual product try-ons and before-and-after visuals for ad campaigns, featuring an interactive carousel to showcase variations.
  * **Film Making Pre-visualization:** A "Director's Panel" that allows creators to instantly apply cinematic moods and character styles to a face, accelerating the creative process.

## Architecture Overview

The application is built with a decoupled frontend and backend architecture, as detailed in the project diagram.

  * **Frontend:** The user interface is built with **HTML, CSS, and JavaScript**, providing an interactive experience for uploading images and manipulating controls.
  * **Backend:** A **Flask API** (`app.py`) serves as the bridge to the backend. The core AI logic resides in `inversion_utils.py`, which orchestrates a pipeline:
    1.  **Preprocessing:** An uploaded image is cropped and resized.
    2.  **HyperStyle Inversion:** The image is converted into a W+ latent vector.
    3.  **GANSpace Editing:** The latent vector is manipulated based on user-defined attributes.
    4.  **StyleGAN2-ADA Synthesis:** The final, edited latent vector is used to generate a new synthetic face.

## Setup and Installation

### Prerequisites

  * Python 3.8+
  * Git
  * NVIDIA GPU with CUDA support (for optimal performance)

### 1\. Clone Project Repositories

First, clone this project's repository. Then, you need to clone the specific model repositories that this project depends on.

```bash
# Clone the main project repository
git clone <your_project_repository_url>
cd <your_project_repository_name>

# Clone the required AI model repositories inside the project directory
git clone https://github.com/yuval-alaluf/hyperstyle.git
git clone https://github.com/NVlabs/stylegan2-ada-pytorch.git
```

### 2\. Download Pre-trained Models

You will need to download the pre-trained AI model weights and place them in the correct directories.

  * **HyperStyle Encoder:** Download `hyperstyle_ffhq.pt` and place it in the `models/hyperstyle/` directory.
  * **StyleGAN2-ADA Generator:** Download `ffhq.pkl` and place it in the `models/stylegan2-ada-pytorch/` directory.
  * **GANSpace Components:** The `download_ganspace_components` function in the code will attempt to download the `ffhq_pca_components.pkl` file automatically when the application is first run.

### 3\. Install Python Packages

It is recommended to use a virtual environment (like `venv` or `conda`). Install the required packages using pip:

```bash
# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
```

Your `requirements.txt` file should include packages like: `flask`, `torch`, `torchvision`, `numpy`, `Pillow`, `face_alignment`.

## How to Run

1.  Once all the repositories are cloned, models are downloaded, and packages are installed, start the Flask web server from your terminal:

    ```bash
    python app.py
    ```

2.  Open your web browser and navigate to the local host address provided in the terminal, which is typically:

    [http://127.0.0.1:5000](https://www.google.com/search?q=http://127.0.0.1:5000)

You can now use the application.
