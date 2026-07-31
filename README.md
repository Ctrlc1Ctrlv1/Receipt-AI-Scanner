# Receipt-AI-Scanner
This project automatically extracts structured information from a photo of a receipt.

Here is the pipeline:
1) Preprocession of the photo(resize, blur, threshold)
2) Dilatation of preprocessed image
3) Get a countour from dilatated image which is simple because the image is already very simplified by preprocessing and dilataion
4) Crop the image using gotten contour
5) Get the text using pytesseract
6) Get a structured-json like information using Gemini
7) Save gotten information in an old json file or create a new one if the last one doesn't exist
