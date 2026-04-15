# Interpreter for the Differently Abled

> A low-cost, two-way communication interpreter bridging the gap between differently-abled individuals and others using **American Sign Language (ASL) Recognition** and **Haptic Feedback** — built on Raspberry Pi.

 **Published Research Paper** — https://ieeexplore.ieee.org/document/9214398
 
 Amrita School of Engineering, Bengaluru, Amrita Vishwa Vidyapeetham

---

##  Overview

This project proposes a two-module interpreter system that enables seamless two-way communication between differently-abled people (blind, deaf, dumb) and others — regardless of the type of sensory disability.

| Module | Direction | Method |
|--------|-----------|--------|
| **Module 1** | Normal Person → Differently Abled | Speech → Text → Haptic Feedback |
| **Module 2** | Differently Abled → Normal Person | ASL Hand Gesture → CNN → Text → Speech |

---

## Tech Stack

| Category | Tools |
|----------|-------|
| Hardware | Raspberry Pi 3B, Pi Camera, USB Microphone, Coin Vibration Motors, LCD Display |
| Language | Python |
| ML Framework | Convolutional Neural Network (CNN) |
| Libraries | OpenCV, TensorFlow/Keras, NumPy |
| Optimizer | ADAM |
| Encoding | 5x5 Tap Method for Haptic Feedback |

---

## 🔧 System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Raspberry Pi 3B                    │
│                                                     │
│  Pi Camera  →  ASL Recognition (CNN)  →  Speech    │
│                                                     │
│  Microphone →  Speech to Text  →  Haptic Feedback  │
└─────────────────────────────────────────────────────┘
```

---

##  Module 1 — Speech to Haptic Feedback

Converts speech from a non-disabled person into haptic vibrations that a differently-abled person can feel using gloves embedded with coin vibration motors.

- Speech recorded via USB microphone
- Converted to text using Python libraries
- Encoded using **5x5 Tap Method** (alphabets + numbers)
- Vibrations delivered via 10 coin motors controlled through de-multiplexer 74LS138

---

##  Module 2 — ASL Gesture Recognition (CNN)

Recognizes American Sign Language hand gestures in real-time using a camera and a trained CNN model.

- Dataset: **4000 images × 29 classes** (26 alphabets + 3 special characters)
- Data augmentation: shearing, rotation, width/height shifts
- Train/Validation split: 90% / 10%
- Optimizer: **ADAM** with **50% Dropout**
- Final Accuracy: **~83%** at 100 epochs
- Output: Predicted text → converted to speech

### CNN Architecture
```
Input → Conv2D + MaxPool2D → Conv2D + MaxPool2D + Dropout(0.5) → FC1 → FC2 → Output (29 classes)
```

---

## 📊 Results

| Epochs | Accuracy | Validation Accuracy |
|--------|----------|-------------------|
| 10 | 65.85% | 70.1% |
| 50 | 78.75% | 77.8% |
| 80 | 80.85% | 75.8% |
| 100 | **83.35%** | **82.3%** |

---

## 🚀 How to Run

```bash
# Clone the repo
git clone https://github.com/saisurya98/Interpreter_for_differently_abled

# Install dependencies
pip install opencv-python tensorflow numpy SpeechRecognition RPi.GPIO

# Run Module 1 (Speech to Haptic)
python module1.py

# Run Module 2 (ASL Recognition)
python module2.py
```

---

## Authors

- **Gorrepati Sai Surya** 
- Priya Prajapati
- M. Nithya

Department of Electrical and Electronics Engineering,
Amrita School of Engineering, Bengaluru, Amrita Vishwa Vidyapeetham, India.

---

## Citation

If you use this work, please cite:
```
Priya Prajapati, Gorrepati Sai Surya, M. Nithya,
"An Interpreter for the Differently Abled Using Haptic Feedback and Machine Learning",
Amrita School of Engineering, Bengaluru, Amrita Vishwa Vidyapeetham, India.
```

---

## License

This project is for academic and research purposes.
