# MOSAIC: Multi-Scale Orientation-Aware Nuclei Segmentation & Centroid Localization

This repository provides the official implementation of **MOSAIC**, a multi-scale, rotation-aware transformer-based framework designed for robust nuclei segmentation and centroid/heatmap prediction in histopathology images (ER-IHC, MoNuSAC, CoNSeP).

The model integrates **hierarchical feature extraction**, **rotation-aware multi-scale fusion**, and **transformer-based long-range reasoning**, enabling accurate segmentation under scale variation, heterogeneous morphology, and rotational distortions.

---

## 📌 Key Features

* **Multi-Scale Patch Extraction**

  * Large: 512×512
  * Medium: 256→512
  * Small: 192→512
  * All scales form parallel training streams.

* **Rotation-Aware Feature Fusion**

  * Designed to maintain robustness across nuclei orientations.

* **Transformer Context Aggregation**

  * Enhances long-range spatial reasoning.

* **Dual Task Prediction**

  * **Semantic segmentation (multi-class or binary)**
  * **Centroid/heatmap estimation for instance separation**

* **Dataset Ready**

  * ER-IHC
  * MoNuSAC
  * CoNSeP

---

## 📁 Repository Structure

```
├── mosaic.ipynb        # Main notebook: preprocessing, model, training, and evaluation
├── /Dataset/           # Example dataset folders (user should add)
└── README.md
```

---

## 🛠️ Requirements

* Python 3.8+
* TensorFlow 2.x / Keras
* NumPy, OpenCV, Matplotlib
* scikit-image, scikit-learn
* tqdm, seaborn

Install using:

```bash
pip install tensorflow numpy opencv-python matplotlib scikit-image scikit-learn seaborn tqdm
```

On **Kaggle**, all dependencies are already available.

---

## ▶️ How to Run

### **Option 1: Kaggle (Recommended)**

1. Upload or open `mosaic.ipynb` in a Kaggle Notebook.
2. Add your dataset(s) as input sources.
3. Update dataset paths inside the notebook:

   ```python
   data_path = "/kaggle/input/your-dataset/"
   ```
4. Enable **GPU** or **TPU**.
5. Run all cells sequentially:

   * Multi-scale patch generation
   * Label and mask preprocessing
   * Model definition (CNN + Transformer fusion)
   * Training
   * Validation & visualization

The best model is automatically saved to:

```
/kaggle/working/MOSAIC_savedmodel/
```

---

### **Option 2: Local Machine**

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-repo>/MOSAIC.git
   cd MOSAIC
   ```
2. Open Jupyter Notebook:

   ```bash
   jupyter notebook mosaic.ipynb
   ```
3. Update dataset paths inside the notebook.
4. Run cells in order.

GPU is strongly recommended for training.

---

## 📊 Outputs

Running MOSAIC will produce:

* Predicted **nuclei segmentation masks**
* Predicted **centroid heatmaps**
* Multi-scale visualization plots
* Quantitative metrics:

  * Dice
  * AJI
  * PQ
  * F1 score
* Trained model folder (`MOSAIC_savedmodel`)

Optional post-processing:

* Watershed-based instance segmentation
* Centroid-guided instance splitting

---

## 📄 Citation

If you use this framework, preprocessing pipeline, or model structure, please cite the MOSAIC publication (update with your final BibTeX once accepted/published):

```bibtex
@article{yourcitation2025mosaic,
  title={MOSAIC: Multi-Scale Orientation-Aware Segmentation and Instance Classification Network},
  author={Sufyan, Arbab and ...},
  journal={Expert Systems with Applications},
  year={2025},
  publisher={Elsevier}
}
```


