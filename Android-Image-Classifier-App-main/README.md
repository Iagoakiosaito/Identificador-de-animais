# Android Image Classifier App

Strongly based on https://github.com/microsoft/onnxruntime-inference-examples/tree/main/mobile/examples/image_classification/android.
Follow their steps to build and run the app.

The main difference of this repo from theirs is that you can pick a picture from your gallery in this implementation, 
while the quantization option was removed.

To use your own classifier app, you must:

- convert your model to ORT format and paste it to `app/src/main/res/raw/`;
- create a txt file with your labels at each line at the same order of the prediction index and paste it to `app/src/main/res/raw/`.
- go to `app/src/main/java/ai/example/app/Mainactivity.kt` and change lines 286 and 291 to your labels 
file name and your model file name, respectively. You may just rename your labels file to "labels.txt" and your model file to "model.ort".

You can change the name of your App at `app/src/main/res/values/strings.xml`.

In order to use it in your phone, you've to click in **Build** -> **Build Bundle(s) / APK(s)** > **Build APK(s)**. 
The apk file'll be located in `project-name/module-name/build/outputs/apk/`.

Example screenshot of a bird species predictor app trained with https://www.kaggle.com/gpiosenka/100-bird-species.

<img width=40% src="images/touchan.jpg" alt="App Screenshot"/>    <img width=40% src="images/ostrich.jpg" alt="App Screenshot"/>

