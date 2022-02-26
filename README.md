# IMAPBotDetection


Credential stuffing is an attack that obtains stolen account credentials, usually sourced from data breaches. It is a technique used to exploit the fact that many people use the same username and password for multiple accounts.
Credential stuffing has become a great matter of concern for the Internet Mail Access Protocol (IMAP), a popular method for accessing electronic mail and news messages maintained on a remote server. A significant vulnerability in IMAP and other legacy email protocols is that it cannot support MFA and depends on only a username and password for authentication, leaving it susceptible to credential stuffing.

As bots generally carry out credential stuffing attacks, a promising countermeasure is to identify and block them before they can login. Our objective is to use two types of behavioral biometrics -  mouse dynamics and keystroke dynamics - to distinguish between bots and humans. In this project,  we introduced a supervised learning bot detection system using mouse and keystroke dynamics and compared the classification of the Random Forest(RF), Decision Tree(DT), Support Vector Machine(SVM), and K-Nearest Neighbors(KNN) machine learning algorithms to identify which model achieves the best overall result.

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

* [**Arash Habibi Lashkari:**](http://ahlashkari.com/index.asp) Supervision
* [**Ashley Sarah Barkworth:**](https://www.linkedin.com/in/ashley-barkworth/) Research and Development (MCS Student)
* [**Rehnuma Tabassum:**](https://www.linkedin.com/in/rehnuma-tabassum-814818175/) Research and Development (MCS Student)
