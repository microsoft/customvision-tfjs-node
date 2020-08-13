# customvision-tfjs-node
Node.js package for TensorFlow.js models exported from Custom Vision Service

If you are looking for a library to use on the browser, please try [customvision-tfjs](https://github.com/microsoft/customvision-tfjs).

## Install
```sh
npm install @microsoft/customvision-tfjs-node
```

## Usage

### Classification
```js
const cvstfjs = require('@microsoft/customvision-tfjs-node');

async function executeAsync(image_filepath) {
  const model = new cvstfjs.ClassificationModel();
  await model.loadModelAsync('file://model.json');
  fs.readFile(image_filepath, function (err, data) {
    if (err) {
      throw err;
    }

    const result = await model.executeAsync(data);
    console.log(result);
  }
}
```

The result is a 1D-array of probabilities.

### Object Detection
```js
const cvstfjs = require('@microsoft/customvision-tfjs-node');

async function executeAsync(image_filepath) {
  const model = new cvstfjs.ObjectDetectionModel();
  await model.loadModelAsync('file://model.json');
  fs.readFile(image_filepath, function (err, data) {
    if (err) {
      throw err;
    }

    const result = await model.executeAsync(data);
    console.log(result);
  }
}
```

The result has 3 arrays.
```js

[
	[[0.1, 0.3, 0.4, 0.3], [0.2, 0.4, 0.8, 0.9]], // bounding boxes (x1, y1, x2, y2)
	[0.2, 0.3], // probabilities
	[1, 4] // class ids
]
```

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
