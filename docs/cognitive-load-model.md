***Load Scoring Logic***


### **1. Overview**

The Load Scoring Logic defines how user interaction signals are converted into a **numerical Cognitive Load Score**, which represents the user's mental effort while interacting with the system.

This score is used to:

- Classify user cognitive state

- Trigger adaptive UI changes in real time

This model is a heuristic-based approximation of cognitive load derived from observable user interaction behavior

### **2. Define formula:**

Cognitive Load Score =

(Click Delay × 2)

\+ (Hesitation Time × 2)

\+ (Backtracking × 3)

\+ (Error Actions × 5)

\+ (Scroll Irregularity × 1)

### **3. Input Normalization (Important)**

To maintain consistency, raw signals should be normalized before applying the formula.

#### **Example:**

- Click Delay → seconds (0--10 scale)

- Hesitation Time → seconds (0--10 scale)

- Backtracking → number of times

- Errors → number of misclicks

- Scroll Irregularity → score (0--5 scale)

**All signals are normalized to a common scale (e.g., 0--10) before scoring to ensure fair contribution across different metrics.**

### 

### **4. Signal Weights Explanation**

Each signal is assigned a weight based on its impact on cognitive load:

| **Signal**          | **Weight** | **Reason**                                                        |
|---------------------|------------|-------------------------------------------------------------------|
| Click Delay         | ×2         | Indicates hesitation but not always severe                        |
| Hesitation Time     | ×2         | duration of inactivity between interactions (no clicks or scroll) |
| Backtracking        | ×3         | Strong indicator of confusion                                     |
| Error Actions       | ×5         | Critical signal of misunderstanding                               |
| Scroll Irregularity | ×1         | Minor indicator of uncertainty                                    |

- **Click Delay** → time between element appearance and user action (click)

- **Hesitation Time** → duration of inactivity between interactions (no clicks or scroll)

- **Scroll Irregularity** → frequency of rapid up/down scroll direction changes within a short time window

### **5. Classification of Cognitive Load**

| **Score Range** | **Cognitive Load Level** | **Interpretation**                |
|-----------------|--------------------------|-----------------------------------|
| 0 -- 30         | Low                      | User is comfortable and confident |
| 31 -- 60        | Medium                   | User shows some hesitation        |
| 61+             | High                     | User is confused or overloaded    |

### **6. Decision Logic**

- **Low Load**

  - No UI changes required

  - Full interface remains visible

- **Medium Load**

  - Minor UI simplifications

  - Highlight key elements

- **High Load**

  - Significant UI simplification

  - Reduce choices

  - Provide guidance

### **7. Example Calculation**

#### **Scenario:**

- Click Delay = 5

- Hesitation Time = 6

- Backtracking = 3

- Error Actions = 2

- Scroll Irregularity = 4

#### **Calculation:**

Score = (5×2) + (6×2) + (3×3) + (2×5) + (4×1)  
= 10 + 12 + 9 + 10 + 4  
= 45

➡️ **Result: Medium Cognitive Load**

### **8. Real-Time Processing Flow**

1.  Tracking Layer collects signals

2.  Values are normalized

3.  Score is calculated using formula

4.  System classifies load level

5.  Result is sent to UI Adapter

6.  UI updates instantly

### **9. Threshold Tuning (Advanced Improvement)**

- Thresholds can be adjusted based on:

  - User testing

  - A/B experiments

  - Different user groups

Example:

- Beginners → lower threshold for "High"

- Experts → higher tolerance

### **10. Limitations**

- Rule-based logic may not capture all behaviors

- The same interaction pattern may represent different cognitive states depending on user experience level and task complexity.

- Requires tuning for accuracy

### **11. Future Enhancements**

- Replace rule-based scoring with Machine Learning models

- Adaptive weights based on user history

- Context-aware scoring (task difficulty, device type)
