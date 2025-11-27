# Dog Breeds Explorer 🐕

An interactive **Bauhaus-styled** data visualization exploring 70 dog breeds using deep learning feature extraction, dimensionality reduction, and D3.js.

![Bauhaus Design](https://img.shields.io/badge/Design-Bauhaus-EBFFAD?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.9+-blue?style=for-the-badge)
![D3.js](https://img.shields.io/badge/D3.js-v7-orange?style=for-the-badge)

## 🎨 Overview

This project visualizes the visual similarities and differences between 70 dog breeds by:
1. **Extracting deep features** from dog images using EfficientNet-B5
2. **Reducing dimensionality** with t-SNE to create 2D embeddings
3. **Interactive visualization** with D3.js in a bold Bauhaus design aesthetic

### Key Features

✨ **Bauhaus Design**: Bold geometric shapes, high contrast black/white/yellow color scheme
🎯 **Interactive Exploration**: Click, zoom, and pan through the dog breed space
📊 **Smart Sampling**: Optimized to show 500 most representative images
🔍 **Detail Popup**: Click any dog to see breed information (positioned near cursor)
🗺️ **Minimap**: Navigate large datasets with ease
📝 **Data Attribution**: Embedded dataset source and methodology explanation

---

## 📦 Setup Instructions

### Prerequisites
- **Python 3.9+** (tested on Python 3.9-3.11)
- Virtual environment (recommended)

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd Dog-breed-data-visualization-
```

### 2. Create and activate virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install required packages
```bash
pip install flask pandas torch torchvision transformers scikit-learn pillow tqdm
```

---

## 🚀 Running the Project

### Quick Start (if data is already processed)

If you already have `static/dog_output_file.csv`:

```bash
python plot_umap.py
```

Then open: **http://localhost:5001**

### Full Pipeline (processing images from scratch)

If you need to process the dog images:

1. **Download the dataset** from [Kaggle - 70 Dog Breeds Image Dataset](https://www.kaggle.com/datasets/gpiosenka/70-dog-breedsimage-data-set)
2. Place the dataset in `static/dogs/`
3. **Run the image processing notebook** to extract features and generate 2D embeddings:
   - Open `image_process.ipynb` in Jupyter
   - Run all cells to generate `static/dog_output_file.csv`
4. **Start the Flask server**:
   ```bash
   python plot_umap.py
   ```

---

## 📁 Project Structure

```
Dog-breed-data-visualization-/
├── static/
│   ├── main.js                 # D3.js visualization logic
│   ├── dogs/                   # Dog images dataset
│   │   ├── train/
│   │   ├── valid/
│   │   ├── test/
│   │   └── dogs.csv
│   └── dog_output_file.csv     # Processed features with x,y coordinates
├── templates/
│   └── index.html              # Bauhaus-styled UI
├── plot_umap.py                # Flask server
├── image_process.ipynb         # Feature extraction & dimensionality reduction
└── README.md
```

---

## 🧠 How It Works

### 1. Feature Extraction
- Uses **EfficientNet-B5** (pre-trained on ImageNet)
- Extracts 2048-dimensional feature vectors from dog images
- Captures visual characteristics: fur texture, body shape, color patterns

### 2. Dimensionality Reduction
- Applies **t-SNE** to reduce 2048D → 2D
- Preserves local structure: similar-looking breeds cluster together
- Alternative: UMAP can be used for faster processing

### 3. Interactive Visualization
- **D3.js** renders images as interactive points
- **Color-coded by breed** for easy identification
- **Zoom & Pan**: Navigate the breed space
- **Click interaction**: Shows breed details at cursor position
- **Minimap**: Overview of entire dataset

---

## 🎨 Design Philosophy

### Bauhaus Aesthetic

Inspired by the **Bauhaus design movement** (1919-1933):

- **Geometric Precision**: Clean lines, bold borders
- **Primary Colors**: Black, white, and #EBFFAD (lime yellow)
- **Typography**: Archivo Black - bold, geometric, uppercase
- **Functionality**: Form follows function
- **High Contrast**: Maximum readability and visual impact

### Color Palette

| Color | Hex Code | Usage |
|-------|----------|-------|
| Lime Yellow | `#EBFFAD` | Primary accent, links, highlights |
| Black | `#000000` | Borders, text, backgrounds |
| White | `#FFFFFF` | Backgrounds, contrast |
| Coral Red | `#FF6B6B` | Secondary accent, shadows |

---

## 🔧 Configuration

### Adjust Number of Displayed Images

In `plot_umap.py`, line 16:

```python
df = df.sample(n=min(500, len(df)), random_state=42)
```

Change `500` to your desired number (e.g., `300` for faster loading, `1000` for more detail).

### Adjust Image Size

In `static/main.js`, lines 58-63:

```javascript
d.w0 = 60;  // Width (default: 60px)
d.h0 = 60;  // Height (default: 60px)
```

Increase for larger points, decrease for denser visualization.

---

## 📊 Dataset Information

### Source
**[70 Dog Breeds Image Dataset](https://www.kaggle.com/datasets/gpiosenka/70-dog-breedsimage-data-set)** from Kaggle

### Statistics
- **70 breeds** total
- **10,000+ images**
- Split into: Train / Validation / Test sets
- Image formats: JPG
- Resolution: Variable (224x224 used for processing)

### Sample Breeds
Afghan, Beagle, Bulldog, Chihuahua, Corgi, Dalmatian, German Shepherd, Golden Retriever, Husky, Labrador, Poodle, Pug, Rottweiler, Shih Tzu, Yorkshire Terrier, and more...

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **Python** | Backend processing |
| **Flask** | Web server |
| **PyTorch** | Deep learning framework |
| **EfficientNet-B5** | Feature extraction model |
| **scikit-learn** | t-SNE dimensionality reduction |
| **D3.js v7** | Interactive visualization |
| **Pandas** | Data manipulation |
| **HTML/CSS** | Bauhaus-styled UI |

---

## 🎯 Features Breakdown

### Visualization Features
- ✅ Interactive zoom and pan
- ✅ Hover to enlarge images
- ✅ Click for detailed breed information
- ✅ Color-coded breed clusters
- ✅ Legend with breed labels
- ✅ Minimap for navigation
- ✅ Responsive design

### Technical Features
- ✅ Deep learning feature extraction
- ✅ Dimensionality reduction (t-SNE)
- ✅ Smart sampling for performance
- ✅ Dynamic popup positioning
- ✅ Bauhaus design system
- ✅ Embedded data attribution

---

## 📝 Notes

### Performance Tips
- **Reduce sample size** if loading is slow (edit `plot_umap.py`)
- **Use smaller images** for faster rendering (adjust `main.js`)
- **Consider UMAP** instead of t-SNE for larger datasets (faster computation)

### Browser Compatibility
- Tested on: Chrome, Firefox, Safari, Edge
- Requires: Modern browser with ES6 support
- Best experience: Chrome/Edge on desktop

---

## 📄 License

Dataset: [Kaggle 70 Dog Breeds Dataset](https://www.kaggle.com/datasets/gpiosenka/70-dog-breedsimage-data-set) © Original Authors

Code: This project is for educational purposes.

---

## 🙏 Acknowledgments

- **Dataset**: gpiosenka on Kaggle
- **Design Inspiration**: Bauhaus movement (1919-1933)
- **Tools**: PyTorch, scikit-learn, D3.js communities

---

## 📧 Contact

For questions or feedback about this project, please open an issue on GitHub.

---

**Built with ❤️ using Python, PyTorch, and D3.js**
