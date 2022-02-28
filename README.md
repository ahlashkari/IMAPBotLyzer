# IMAP Bot AnaLyzer (IMAPBotLyzer)


Credential stuffing is an attack that obtains stolen account credentials, usually sourced from data breaches. It is a technique used to exploit the fact that many people use the same username and password for multiple accounts.
Credential stuffing has become a great matter of concern for the Internet Mail Access Protocol (IMAP), a popular method for accessing electronic mail and news messages maintained on a remote server. A significant vulnerability in IMAP and other legacy email protocols is that it cannot support MFA and depends on only a username and password for authentication, leaving it susceptible to credential stuffing.

As bots generally carry out credential stuffing attacks, a promising countermeasure is to identify and block them before they can login. Our objective is to use two types of behavioral biometrics -  mouse dynamics and keystroke dynamics - to distinguish between bots and humans. In this project,  we introduced a supervised learning bot detection system using mouse and keystroke dynamics and compared the classification of the Random Forest(RF), Decision Tree(DT), Support Vector Machine(SVM), and K-Nearest Neighbors(KNN) machine learning algorithms to identify which model achieves the best overall result.


### Extracted Features

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
6. Number of events
7. Curvature
8. Maximum deviation
9. Sum of angles
10. Click time(PC actions)

After computing the set of features values for each mouse and keystroke feature, the average, standard deviation, maximum, and minimum values are calculated over each set. In the end, a total of 131 features are calculated from keystroke and mouse movements which are:

#### Keystroke

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


#### Mouse
* num_actions
* total_duration
* mm_avg_v
* mm_sd_v
* mm_max_v
* mm_min_v
* mm_avg_a
* mm_sd_a
* mm_max_a
* mm_min_a
* mm_avg_j
* mm_sd_j
* mm_max_j
* mm_min_j
* mm_avg_duration
* mm_sd_duration
* mm_max_duration
* mm_min_duration
* mm_avg_straightness
* mm_sd_straightness
* mm_max_straightness
* mm_min_straightness
* mm_avg_num_points
* mm_sd_num_points
* mm_max_num_points
* mm_min_num_points
* mm_avg_curvature
* mm_sd_curvature
* mm_max_curvature
* mm_min_curvature
* mm_avg_angle_sum
* mm_sd_angle_sum
* mm_max_angle_sum
* mm_min_angle_sum
* mm_avg_max_deviation
* mm_sd_max_deviation
* mm_max_max_deviation
* mm_min_max_deviation
* pc_avg_v
* pc_sd_v
* pc_max_v
* pc_min_v
* pc_avg_a
* pc_sd_a
* pc_max_a
* pc_min_a
* pc_avg_j
* pc_sd_j
* pc_max_j
* pc_min_j
* pc_avg_duration
* pc_sd_duration
* pc_max_duration
* pc_min_duration
* pc_avg_straightness
* pc_sd_straightness
* pc_max_straightness
* pc_min_straightness
* pc_avg_num_points
* pc_sd_num_points
* pc_max_num_points
* pc_min_num_points
* pc_avg_curvature
* pc_sd_curvature
* pc_max_curvature
* pc_min_curvature
* pc_avg_angle_sum
* pc_sd_angle_sum
* pc_max_angle_sum
* pc_min_angle_sum
* pc_avg_max_deviation
* pc_sd_max_deviation
* pc_max_max_deviation
* pc_min_max_deviation
* pc_avg_click_time
* pc_sd_click_time
* pc_max_click_time
* pc_min_click_time
* dd_avg_v
* dd_sd_v
* dd_max_v
* dd_min_v
* dd_avg_a
* dd_sd_a
* dd_max_a
* dd_min_a
* dd_avg_j
* dd_sd_j
* pc_max_j
* pc_min_j
* dd_avg_duration
* dd_sd_duration
* dd_max_duration
* dd_min_duration
* dd_avg_straightness
* dd_sd_straightness
* dd_max_straightness
* dd_min_straightness
* dd_avg_num_points
* dd_sd_num_points
* dd_max_num_points
* dd_min_num_points
* dd_avg_curvature
* dd_sd_curvature
* dd_max_curvature
* dd_min_curvature
* dd_avg_angle_sum
* dd_sd_angle_sum
* dd_max_angle_sum
* dd_min_angle_sum
* dd_avg_max_deviation
* dd_sd_max_deviation
* dd_max_max_deviation
* dd_min_max_deviation



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
* [**Ashley Sarah Barkworth:**](https://www.linkedin.com/in/ashley-barkworth/) Research and Development (MCS student)
* [**Rehnuma Tabassum:**](https://www.linkedin.com/in/rehnuma-tabassum-814818175/) Research and Development (MCS student)
