# IMAPBotDetection

## Overview 

___

There are multiple modules in the program:
* `app` is the GUI with the three tasks to complete, namely:
  * Typing a specified word 10 times
  * Clicking a moving ball 10 times
  * Sorting 8 fruits and animals into boxes
* `bot` contains two bot scripts that are meant to be run simultaneously with the GUI program to complete the tasks automatically
* `feature_extraction` calculates the various mouse and keystroke features from the user's mouse and keystroke data
* `classification` creates the feature data sets, implements the learning algorithms, and runs the cross validation to calculate four scores:
  * Precision
  * Recall
  * Accuracy
  * F-score
* `util` contains helper functions

## Dependencies 

___

* Pillow 
* PyAutoGUI
* Matplotlib 
* NumPy 
* OpenCV 
* Pandas 
* pynput 
* Scikit-learn
* SciPy 

## How to Use

___

### Running the app
To run the app without the bots:
```shell
python3 app/app.py human 
```
To run the app with the simple bot, open two terminal windows or tabs:
```shell
# Run this in the first window/tab
python3 app/app.py simple
# Run this in the second window/tab
python3 bot/simple_bot.py
```
Similarly, to run the app with the advanced bot:
```shell
# Run this in the first window/tab
python3 app/app.py advanced
# Run this in the second window/tab
python3 bot/advanced_bot.py
```

The mouse and keystroke data are saved under **data/events/**.

### Running the Feature Extraction
```shell
python3 feature_extraction/extract_features.py
```

The mouse and keystroke features are saved under **data/features***.

### Running the cross validation
```shell
python3 classification/classification.py

```
### Project Team members

* [**Arash Habibi Lashkari:**](http://ahlashkari.com/index.asp) Supervisor
* [**Ashley Sarah Barkworth:**](https://www.linkedin.com/in/ashley-barkworth/) Research and Development (MCS Student)
* [**Rehnuma Tabassum:**](https://www.linkedin.com/in/rehnuma-tabassum-814818175/) Research and Development (MCS Student)
