


# 🎬 Converting Colored Video to Grayscale Using OpenCV

This project demonstrates how to convert a colored video into grayscale using **OpenCV** in Python. It's perfect for preprocessing in computer vision, reducing file size, or achieving a classic black-and-white aesthetic.



---

## 🧰 Requirements

Install OpenCV:

```bash
pip install opencv-python
```

> If you're using Google Colab, mount your Google Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```

---

## 🗂️ Folder Structure

```
video/
├── input_video.mp4         # Original colored video
└── output_grayscale.avi    # Grayscale output video
assets/
└── preview.gif             # Optional preview GIF
```

---

## 🧠 How It Works

### 🔹 Step 1: Validate Input Path  
Ensures the input video file exists.

### 🔹 Step 2: Read Video  
Uses `cv2.VideoCapture()` to read the video frame-by-frame.

### 🔹 Step 3: Convert to Grayscale  
Each frame is converted using `cv2.COLOR_BGR2GRAY`.

### 🔹 Step 4: Save Output  
Writes the grayscale frames to a new video using `cv2.VideoWriter()`.


## 🧪 Usage

Update your paths and run this script:

```python
# Mount Google Drive (if using Colab)
from google.colab import drive
drive.mount('/content/drive')

# Required Libraries
import cv2
from pathlib import Path

# Conversion Function
def convert_video_to_grayscale(input_video_path, output_video_path):
    input_path = Path(input_video_path)
    if not input_path.is_file():
        print(" Error: Input video file not found.")
        return

    cap = cv2.VideoCapture(str(input_path))
    if not cap.isOpened():
        print(" Failed to open the video.")
        return

    width  = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
    height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
    fps    = cap.get(cv2.CAP_PROP_FPS)
    codec  = cv2.VideoWriter_fourcc(*'XVID')

    out = cv2.VideoWriter(str(output_video_path), codec, fps, (width, height), isColor=False)

    print(f" Converting video to grayscale...\nInput: {input_video_path}\nOutput: {output_video_path}")

    while True:
        ret, frame = cap.read()
        if not ret:
            break
        gray_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        out.write(gray_frame)

    cap.release()
    out.release()
    print("Conversion complete! Grayscale video saved successfully.")

# Run It
if __name__ == "__main__":
    print(" Grayscale Video Converter")
    input_video = "/content/drive/MyDrive/videos(b/w)/input_video.mp4"
    output_video = "/content/drive/MyDrive/videos(b/w)/output_grayscale.avi"
    convert_video_to_grayscale(input_video, output_video)
```

Output in the terminal:
```
🎬 Grayscale Video Converter
🎞️ Converting video to grayscale...
✅ Conversion complete! Grayscale video saved successfully.
```

---

## 🧾 Credits

Crafted by **Gurpinder** using Python and OpenCV 💡





