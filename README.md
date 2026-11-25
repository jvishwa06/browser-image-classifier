# Browser Image Classifier

Classify an image in your browser with TensorFlow.js. Nothing is uploaded to a server.

## Image classification page

`index.html` and `inference.js` load the pre-trained **MobileNet** model from `@tensorflow-models/mobilenet`. Choose an image file, preview it, and press **Classify Image** to see the predictions.

To use it, open `index.html` in a browser, or serve the folder with any static file server. TensorFlow.js and MobileNet are loaded from the jsDelivr CDN.

## MNIST training script

`train.js` is a separate script that trains a small digit classifier with `@tensorflow/tfjs`:

- Data: 5,000 images from the MNIST dataset (`tf.data.mnist()`), reshaped to 28x28x1.
- Model: Conv2D (32 filters, 3x3, ReLU), MaxPooling2D, Flatten, Dense (128, ReLU), Dense (10, softmax).
- Training: Adam optimiser, categorical cross-entropy, 10 epochs, batch size 32.
- Output: saves the model as `mnist-model` through a browser download.

`train.js` imports `@tensorflow/tfjs` as an ES module, so it needs a bundler or module setup. The classification page does not use the trained model.

## Dependencies

```bash
npm install
```

`package.json` lists `@tensorflow/tfjs` and `@tensorflow-models/mobilenet`.
