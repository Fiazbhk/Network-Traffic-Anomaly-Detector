# Network Traffic Anomaly Detector

A network traffic anomaly detection system built using the KDD Cup 1999 dataset. The project uses statistical thresholds to identify attack connections in network traffic data and achieves 97 percent overall accuracy.

---

## Project Overview

This project analyzes network connection records and classifies each connection as either normal or an attack. Instead of using complex machine learning models, the detector works by learning the behavior of normal traffic and flagging anything that deviates significantly from it.

The project was built entirely in Google Colab using Python.

---

## Dataset

- **Source:** KDD Cup 1999 Dataset
- **Platform:** [Kaggle - galaxyh/kdd-cup-1999-data](https://www.kaggle.com/datasets/galaxyh/kdd-cup-1999-data)
- **File used:** kddcup.data_10_percent_corrected
- **Total records:** 494,021
- **Normal connections:** 97,278
- **Attack connections:** 396,743
- **Features:** 42 (16 selected for detection)

---

## How It Works

1. Load the dataset and assign column names
2. Label each connection as normal or attack
3. Select 16 numeric features for analysis
4. Calculate the mean and standard deviation of each feature using only normal traffic
5. Set the detection threshold for each feature as mean plus 3 standard deviations
6. Flag any connection that exceeds the threshold on any feature as an attack
7. Evaluate results using precision, recall, F1 score, and a confusion matrix

---

## Results

| Metric | Attack | Normal | Overall |
|--------|--------|--------|---------|
| Precision | 97% | 95% | 97% |
| Recall | 99% | 88% | - |
| F1 Score | 98% | 92% | 95% |
| Accuracy | - | - | 97% |

**Confusion Matrix**

| | Predicted Attack | Predicted Normal |
|---|---|---|
| Actual Attack | 392,388 | 4,355 |
| Actual Normal | 11,461 | 85,817 |

---

## Key Findings

- Attack traffic has a much higher connection count (average 411) compared to normal traffic (average 8)
- Attackers send more data to the target but receive very little back
- Attack connections are significantly shorter in duration
- SYN error rates are much higher in attack traffic, indicating connection flooding behavior

---

## Tools and Technologies

| Tool | Purpose |
|------|---------|
| Python 3 | Programming language |
| Pandas | Data loading and analysis |
| Scikit-learn | Model evaluation metrics |
| Matplotlib | Bar chart visualizations |
| Seaborn | Confusion matrix heatmap |
| Kaggle API | Dataset download in Colab |
| Google Colab | Development environment |

---

## Project Structure

```
Network_Traffic_Anomaly_Detector/
│
├── Network_Traffic_Anomaly_Detector.ipynb    # Main notebook
├── README.md                                 # Project documentation
└── Report.docx                               # Detailed project report
```

---

## How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Upload the notebook file `Network_Traffic_Anomaly_Detector.ipynb`
3. Get your Kaggle API key from [kaggle.com/settings](https://www.kaggle.com/settings)
4. Run the cells in order from top to bottom
5. Upload your `kaggle.json` file when prompted in the setup cell

---

## Limitations

- The threshold method checks each feature independently and does not capture relationships between features
- Some normal connections are incorrectly flagged as attacks (11,461 false positives)
- Thresholds are based on the training data and may need adjustment for different network environments

---

## Future Improvements

- Apply machine learning models such as Random Forest or Isolation Forest
- Reduce false positives by combining multiple threshold conditions
- Build a real-time detection dashboard
- Test on the full KDD Cup dataset for a more complete evaluation

---

## References

- KDD Cup 1999 Data: http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html
- Kaggle Dataset: https://www.kaggle.com/datasets/galaxyh/kdd-cup-1999-data
