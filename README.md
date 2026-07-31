# Receipt-AI-Scanner
This project automatically extracts structured information from a photo of a receipt.

The project combines:

- OpenCV for receipt detection and perspective correction.
- Tesseract OCR for text extraction.
- Gemini for converting noisy OCR output into structured JSON and extracting receipt information such as purchased items, dates, totals, and taxes.

## Pipeline
1. Load the receipt image.
2. Preprocess the image by resizing, converting it to grayscale, applying Gaussian blur, and thresholding.
3. Apply morphological dilation to connect fragmented regions and simplify contour detection.
4. Detect the receipt contour and identify its four corner points.
5. Apply a perspective transformation to obtain a top-down view of the receipt.
6. Extract the text from the corrected image using Tesseract OCR.
7. Use Gemini to convert the extracted text into structured JSON.
8. Save the extracted information to a JSON file, creating the file if it does not already exist.

Example of contour detection:
<img width="1610" height="451" alt="download" src="https://github.com/user-attachments/assets/6b0b1567-8798-4543-9eae-4e3343ff5ace" />


## Example Output
```json
[
{
        "store_name": "Walmart",
        "purchase_date": "2023-10-19",
        "currency": "USD",
        "items": [
            {
                "name": "Mt",
                "price": 14.98
            },
            {
                "name": "WHL POT",
                "price": 0.96
            },
            {
                "name": "WHL POT",
                "price": 0.96
            },
            {
                "name": "MC LEM MERG",
                "price": 5.97
            },
            {
                "name": "GREEN ONIONS",
                "price": 0.88
            },
            {
                "name": "GM 20 GLOVE",
                "price": 3.97
            },
            {
                "name": "SCOTT SINGLE",
                "price": 2.87
            },
            {
                "name": "FRAM OTL EG",
                "price": 4.56
            },
            {
                "name": "WALMART PLAS",
                "price": -10.0
            }
        ],
        "tax": 5.69,
        "total": 73.8
    }

]
```
## Technologies

- Python
- OpenCV
- NumPy
- Tesseract OCR
- Google Gemini API
