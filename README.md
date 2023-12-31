# Combining identity features and artifact analysis for Differential Morphing Attack Detection

This is the repository that holds the official reference implementation for the paper "Combining identity features and artifact analysis for Differential Morphing Attack Detection" (Di Domenico et al., 2023).


## Requirements

The required packages are present in the `requirements.txt` file. To install them, run the following command:

```bash
pip install -r requirements.txt
```

## Usage

The `iciap_2023` package exposes a `get_prediction` function which, in its simplest form, takes in input a document and a live image, and returns a morphing prediction.
0 means that the document image is bona fide, while 1 means that the document image is morphed.

```python
from iciap_2023 import get_prediction
import cv2 as cv

# Load the document and the live image
document = cv.imread("document.png")
live = cv.imread("live.png")

# Get the prediction
prediction = get_prediction(document, live)
```

This function also allows the user to specify the device to use for the computation (i.e. CPU or GPU) with the optional `device` parameter. The default value is `cpu`.

```python
from iciap_2023 import get_prediction
import cv2 as cv

# Load the document and the live image
document = cv.imread("document.png")
live = cv.imread("live.png")

# Get the prediction
prediction = get_prediction(document, live, device="cuda:0")
```

Finally, the function supports computing batched predictions, by passing two lists of equal length: one containing the documents and the other containing the live images. The function will return a list of predictions.

```python
from iciap_2023 import get_prediction
import cv2 as cv

# Load the documents and the live images
documents = [cv.imread("document1.png"), cv.imread("document2.png")]
lives = [cv.imread("live1.png"), cv.imread("live2.png")]

# Get the predictions
predictions = get_prediction(documents, lives, device="cuda:0")
```

## Acknowledgement

When using the code from this repository, please cite the following work:

```
@inproceedings{di2023combining,
  title={Combining Identity Features and Artifact Analysis for Differential Morphing Attack Detection},
  author={Di Domenico, Nicol{\`o} and Borghi, Guido and Franco, Annalisa and Maltoni, Davide},
  booktitle={International Conference on Image Analysis and Processing},
  pages={100--111},
  year={2023},
  organization={Springer}
}
```
