
# Read Circle Radius Script (OpenCV)
## Description
This project is designed to process and analyze images within a specified folder by calculating the radius of the minimum enclosing circle for each contour detected in the image, displaying the radius for each image in the program's output.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

## Installation
Install [PyCharm Community Edition](https://www.jetbrains.com/pycharm/download/?section=windows)

## Usage
To use the script, you need to provide the path to the test image folder containing the traffic light images.

    1. Update the test_folder variable in the script with the appropriate path.
    2. Run the script:

### Example
    
    import cv2
    import numpy as np
    import os

    test_folder = "/path/to/your/test/folder"

    for filename in os.listdir(test_folder):
        image_path = os.path.join(test_folder, filename)
        image = cv2.imread(image_path)
        gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
        _, thresh = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)
        contours, _ = cv2.findContours(thresh, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
        for contour in contours:
            x, y, w, h = cv2.boundingRect(contour)
            area = cv2.contourArea(contour)
            (x, y), radius = cv2.minEnclosingCircle(contour)
            print(f"Radius of {filename}: {radius}")


## License
This project is licensed under the [MIT License](https://www.mit.edu/~amini/LICENSE.md).



