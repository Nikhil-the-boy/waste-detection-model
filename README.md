# 🧠 RealWaste Detection Model (ResNet18 + PyTorch)

This project is a deep learning-based image classifier that uses **transfer learning with ResNet18** to detect different types of waste materials from the **RealWaste** dataset. The goal is to assist in smart waste management by helping machines automatically identify the category of waste for better recycling.

---

## 📦 Waste Categories

The model classifies images into the following 9 real-world waste types:

- 📦 Cardboard  
- 🍎 Food Organics  
- 🍶 Glass  
- 🥫 Metal  
- 🗑️ Miscellaneous Trash  
- 📄 Paper  
- 🧴 Plastic  
- 👕 Textile Trash  
- 🌿 Vegetation  

These classes come directly from the [RealWaste dataset](https://archive.ics.uci.edu/dataset/908/realwaste).

---

## 📁 Dataset

The dataset is automatically downloaded and extracted using this command:
```bash
wget -O realwaste.zip "https://archive.ics.uci.edu/static/public/908/realwaste.zip"
unzip realwaste.zip -d realwaste_data
```

Folder structure:
realwaste_data/realwaste-main/RealWaste/
├── Cardboard/
├── Food Organics/
├── Glass/
├── Metal/
├── Miscellaneous Trash/
├── Paper/
├── Plastic/
├── Textile Trash/
└── Vegetation/


** Model Architecture:
I use a pretrained ResNet18 model from PyTorch and only fine-tune the last layer to adapt to the 9 waste categories.
- Pretrained backbone: ResNet18
- Final Layer: nn.Linear(512, 9)
- Optimizer: Adam with lr=0.001
- Loss: CrossEntropyLoss
- Augmentations:
- Resize to 128x128
- Random horizontal flip
- Random rotation (15°)
- Brightness jitter
- Normalization

** Training & Evaluation:
* Dataset is split into 80% training and 20% testing
* Training and validation are done using standard PyTorch DataLoaders
* Results are printed in terms of class-wise predictions and total accuracy

** Limitations: 
- The dataset size is small, so the model might not generalize well to unseen or real-world scenarios.
- It may struggle with classes that look visually similar (e.g. plastic vs. paper).
- The model is sensitive to lighting and background conditions despite using augmentations.
- Currently, it only supports image input — no real-time webcam or video processing is implemented.
- It is not deployed to a web or mobile interface yet.
- Model performance could be improved further with hyperparameter tuning and better validation techniques.

|| Feel free to fork this repo or open an issue if you'd like to contribute or give feedback. Star ⭐ if this helped you!||

-  Author
Nikhil Kumar
GitHub: Nikhil-the-boy
