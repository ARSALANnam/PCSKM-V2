# PCSKM-V2

# 🎨 Smart K-Means Image Compressor

A Python-based image compression tool that uses **K-Means Clustering** and **Machine Learning** to intelligently reduce image file size while maintaining structural quality.

Unlike standard compressors, this tool **automatically finds the optimal number of colors (k)** by analyzing the Structural Similarity Index (SSIM) and applying an adaptive thresholding algorithm.

## 🚀 Key Features

* **Adaptive K-Optimization:** Automatically determines the best `k` (number of clusters) for each specific image.
* **Quality Assurance:** Uses **SSIM (Structural Similarity Index)** to ensure the compressed image looks like the original.
* **Smart Early Stopping:** Stops processing when target quality is reached or when increasing `k` yields diminishing returns (saving computational time).
* **Detailed Analytics:** precise calculation of compression ratio, size reduction percentage, and processing time.
* **Visual Comparison:** Generates side-by-side comparison of the Original vs. Compressed image.

## 🛠️ Installation

1.  Clone the repository:
    ```bash
    git clone [https://github.com/YOUR_USERNAME/smart-kmeans-compressor.git](https://github.com/YOUR_USERNAME/smart-kmeans-compressor.git)
    cd smart-kmeans-compressor
    ```

2.  Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## 📋 Requirements

* Python 3.x
* OpenCV (`opencv-python`)
* NumPy (`numpy`)
* Matplotlib (`matplotlib`)
* Scikit-Learn (`scikit-learn`)
* Scikit-Image (`scikit-image`)

## 💻 Usage

1.  Place your target image in the project folder (e.g., named `test.jpeg`).
2.  Open the script and ensure the image path matches your file.
3.  Run the script:

    ```bash
    python main.py
    ```

4.  The script will output the logs in the console and save the result as `compressed_smart.jpg`.

## 🧠 How It Works ( The Logic)

The core of this project is the `find_optimal_k` algorithm. Instead of guessing a fixed `k` (e.g., k=64), the script performs an iterative search:

1.  **Candidates:** It tests a range of `k` values: `[4, 8, 12, 16, 24, 32, 48, 64]`.
2.  **Fast Evaluation:** Uses a lightweight K-Means initialization (`n_init=3`) for rapid testing.
3.  **SSIM Calculation:** For each `k`, it reconstructs the image and calculates the SSIM score against the original.
4.  **Decision Making:**
    * **Target Reached:** If `SSIM >= 0.92` (configurable), it stops and selects that `k`.
    * **Diminishing Returns:** If increasing `k` improves SSIM by less than `0.5%`, it stops to prevent unnecessary processing.

## 📊 Results Example

| Metric | Value |
| :--- | :--- |
| **Optimal K** | 24 |
| **Original Size** | 2.5 MB |
| **Compressed Size** | 1.4 MB |
| **Size Reduction** | ~44% |
| **SSIM Score** | 0.92 |


## 📝 License

This project is open-source 
