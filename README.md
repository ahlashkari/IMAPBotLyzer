# IMAP Bot AnaLyzer (IMAPBotLyzer)

Credential stuffing is an attack that obtains stolen account credentials, usually sourced from data breaches. It is a technique used to exploit the fact that many people use the same username and password for multiple accounts.
Credential stuffing has become a great matter of concern for the Internet Mail Access Protocol (IMAP), a popular method for accessing electronic mail and news messages maintained on a remote server. A significant vulnerability in IMAP and other legacy email protocols is that it cannot support MFA and depends on only a username and password for authentication, leaving it susceptible to credential stuffing.

As bots generally carry out credential stuffing attacks, a promising countermeasure is to identify and block them before they can login. Our objective is to use two types of behavioral biometrics -  mouse dynamics and keystroke dynamics - to distinguish between bots and humans. In this project,  we introduced a supervised learning bot detection system using mouse and keystroke dynamics and compared the classification of the Random Forest(RF), Decision Tree(DT), Support Vector Machine(SVM), and K-Nearest Neighbors(KNN) machine learning algorithms to identify which model achieves the best overall result.


## Extracted Features

To distinguish between human and bot, A GUI is developed to capture key and mouse events from both bot and human. Four temporal features are extracted from keystroke data which are:

1. Hold time
2. Inter-key Latency
3. Press time
4. Release time

To extract mouse features, the mouse events are parsed and grouped to form actions. The type of actions are: Mouse move(MM), Point and Click(PC), and Drag and Drop(DD). From each action, ten features are extracted which are:

1. Tangential velocity
2. Acceleration
3. Jerk
4. Duration
5. Straightness
6. Number of events(points)
7. Curvature
8. Maximum deviation
9. Sum of angles
10. Click time(PC actions)

After computing the set of features values for each mouse and keystroke feature, the average, standard deviation, maximum, and minimum values are calculated over each set of actions. Three additional features are calculated: the total time taken to complete the typing activity; the total time taken to complete the mouse activities; and the total number of mouse actions. In the end, a total of 131 features are calculated from keystroke and mouse movements which are:

### Keystroke:

* Total time taken (typing activity)
* Average hold time
* Max hold time
* Min hold time
* SD hold time
* Average CPR time
* Max CPR time
* Min CPR time
* SD CPR time
* Average Release Latency
* Max Release Latency
* Min Release Latency
* SD Release Latency
* Average Press Latency
* Max Press Latency
* Min Press Latency
* SD Press Latency


### Mouse:

* Total number of mouse actions (MM, PC, and DD)
* Total time taken (mouse activities)
* Average Velocity (MM actions)
* SD Velocity (MM actions)
* Max Velocity (MM actions)
* Min Velocity (MM actions)
* Average Acceleration (MM actions)
* SD Acceleration (MM actions)
* Max Acceleration (MM actions)
* Min Acceleration (MM actions)
* Average Jerk (MM actions)
* SD Jerk (MM actions)
* Max Jerk (MM actions)
* Min Jerk (MM actions)
* Average Duration (MM actions)
* SD Duration (MM actions)
* Max Duration (MM actions)
* Min Duration (MM actions)
* Average Straightness (MM actions)
* SD Straightness (MM actions)
* Max Straightness (MM actions)
* Min Straightness (MM actions)
* Average Number of Points (MM actions)
* SD Number of Points (MM actions)
* Max Number of Points (MM actions)
* Min Number of Points (MM actions)
* Average Curvature (MM actions)
* SD Curvature (MM actions)
* Max Curvature (MM actions)
* Min Curvature (MM actions)
* Average Sum of Angles (MM actions)
* SD Sum of Angles (MM actions)
* Max Sum of Angles (MM actions)
* Min Sum of Angles (MM actions)
* Average Max Deviation (MM actions)
* SD Max Deviation (MM actions)
* Max Max Deviation (MM actions)
* Min Max Deviation (MM actions)
* Average Velocity (PC actions)
* SD Velocity (PC actions)
* Max Velocity (PC actions)
* Min Velocity (PC actions)
* Average Acceleration (PC actions)
* SD Acceleration (PC actions)
* Max Acceleration (PC actions)
* Min Acceleration (PC actions)
* Average Jerk (PC actions)
* SD Jerk (PC actions)
* Max Jerk (PC actions)
* Min Jerk (PC actions)
* Average Duration (PC actions)
* SD Duration (PC actions)
* Max Duration (PC actions)
* Min Duration (PC actions)
* Average Straightness (PC actions)
* SD Straightness (PC actions)
* Max Straightness (PC actions)
* Min Straightness (PC actions)
* Average Number of Points (PC actions)
* SD Number of Points (PC actions)
* Max Number of Points (PC actions)
* Min Number of Points (PC actions)
* Average Curvature (PC actions)
* SD Curvature (PC actions)
* Max Curvature (PC actions)
* Min Curvature (PC actions)
* Average Sum of Angles (PC actions)
* SD Sum of Angles (PC actions)
* Max Sum of Angles (PC actions)
* Min Sum of Angles (PC actions)
* Average Max Deviation (PC actions)
* SD Max Deviation (PC actions)
* Max Max Deviation (PC actions)
* Min Max Deviation (PC actions)
* Average Click Time (PC actions)
* SD Click Time (PC actions)
* Max Click Time (PC actions)
* Min Click Time (PC actions)
* Average Velocity (DD actions)
* SD Velocity (DD actions)
* Max Velocity (DD actions)
* Min Velocity (DD actions)
* Average Acceleration (DD actions)
* SD Acceleration (DD actions)
* Max Acceleration (DD actions)
* Min Acceleration (DD actions)
* Average Jerk (DD actions)
* SD Jerk (DD actions)
* Max Jerk (DD actions)
* Min Jerk (DD actions)
* Average Duration (DD actions)
* SD Duration (DD actions)
* Max Duration (DD actions)
* Min Duration (DD actions)
* Average Straightness (DD actions)
* SD Straightness (DD actions)
* Max Straightness (DD actions)
* Min Straightness (DD actions)
* Average Number of Points (DD actions)
* SD Number of Points (DD actions)
* Max Number of Points (DD actions)
* Min Number of Points (DD actions)
* Average Curvature (DD actions)
* SD Curvature (DD actions)
* Max Curvature (DD actions)
* Min Curvature (DD actions)
* Average Sum of Angles (DD actions)
* SD Sum of Angles (DD actions)
* Max Sum of Angles (DD actions)
* Min Sum of Angles (DD actions)
* Average Max Deviation (DD actions)
* SD Max Deviation (DD actions)
* Max Max Deviation (DD actions)
* Min Max Deviation (DD actions)


## Overview


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

## Copyright (c) 2022 

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (IMAPBotLyzer), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
 
For citation in your works and also understanding IMAPBotLyzer completely, you can find below published paper:

"Detecting IMAP Credential Stuﬃng Bots Using Behavioural Biometrics", Ashley Barkworth, Rehnuma Tabassum and Arash Habibi Lashkari, The ACM Symposium on Access Control Models and Technologies (ACM SACMAT 2022), Arizona, USA, 2022 (Submitted)
```

## Project Team members

* [**Arash Habibi Lashkari:**](http://ahlashkari.com/index.asp) Supervisor
* [**Ashley Sarah Barkworth:**](https://www.linkedin.com/in/ashley-barkworth) Research and Development (MCS student)
* [**Rehnuma Tabassum:**](https://www.linkedin.com/in/rehnuma-tabassum-814818175) Research and Development (MCS student)
