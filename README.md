# CVLabAssignment01_Lab04
# Skin Lesion Boundary Detection Using Canny Edge Detection

## Objective
Detect the boundary of a skin lesion using classical image filtering and Canny edge
detection, and evaluate how effectively edge detection separates the lesion from
surrounding skin.

## Pipeline
`Original → Grayscale → Gaussian Filter → Canny Edge Detection → Lesion Boundary`

## Dataset
5 representative images (one per class) from the same HAM10000-derived subset used in
previous labs: Melanoma, Melanocytic nevus, Benign keratosis, Dermatofibroma, Vascular lesion.

## Method
- Canny tested at 3 threshold pairs: 50–100, 100–200, 150–250
- Best threshold auto-selected per image via a boundary-closure quality score
- Morphological closing + largest-contour extraction → lesion boundary, area, perimeter
- 8-way comparison: {Original, Average, Gaussian, Median} × {Sobel, Canny}

## Results Summary

| Image | Best Filter | Edge Method | Area (px) | Perimeter (px) |
|---|---|---|---|---|
| Melanoma | Gaussian | Canny 50-100 | 782086.0 | 3574.0 |
| Melanocytic nevus | Gaussian | Canny 50-100 | 6133.5 | 4092.2 |
| Benign keratosis | Gaussian | Canny 50-100 | 49424.5 | 3078.6 |
| Dermatofibroma | Gaussian | Canny 50-100 | 393.0 | 133.9 |
| Vascular lesion | Gaussian | Canny 50-100 | 594.5 | 237.9 |

 **Known issue:** the Melanoma result captured ~100% of the image frame (a detection
failure, not an actual lesion boundary) — see the full report for analysis and proposed fixes.

Across the 8-way comparison, **Original + Canny** and **Median + Canny** performed best
overall; **Average + Canny** and **Gaussian + Canny** performed worst.

## Repository Structure
```
Lab03_Canny_Boundary_Detection/
├── Lab_Canny_Lesion_Boundary.ipynb     
├── Lab_Canny_Boundary_Filled.pdf      
└── README.md
```

## How to Run
1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Run all cells; upload the dataset zip when prompted.
3. Insert the generated figures into the report, review/adjust the Q&A as needed.

## License
Academic use only, as part of a Computer Vision lab assignment.
