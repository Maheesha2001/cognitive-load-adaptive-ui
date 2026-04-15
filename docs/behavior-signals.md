***Behavior Signals***


### **1. Click Delay** 

- **Definition:**

> Time taken by the user to click on a specific interactive element **after it becomes visible or after the previous interaction**.

- **Interpretation:**

  - Short delay → Confident, quick decision

  - Long delay → User is thinking before taking a specific action

### **2. Scroll Behavior** 

- **Definition:**  
  Speed and pattern of user scrolling

- **Interpretation:**

  - Fast scrolling → Low engagement / scanning

  - Slow scrolling + pauses → potential confusion or high cognitive processing

  - Irregular scrolling (up/down repeatedly) → Uncertainty

### **3. Backtracking** 

- **Definition:**  
  User navigates back to previously visited pages or sections repeatedly

- **Interpretation:**

  - Indicates difficulty in decision-making

  - Suggests information overload or lack of clarity

### **4. Errors (Interaction Corrections)** 

- **Definition:**

> Repeated interactions where the user selects multiple different elements before making a final decision.

- **Examples:**

  - Clicking several products in quick succession before choosing one

  - Selecting different filter options repeatedly

  - Changing selections multiple times

<!-- -->

- **Interpretation:**

  - Indicates uncertainty in decision-making

  - Suggests difficulty comparing options or understanding information

### **5. Hesitation (Inactivity)**

- **Definition:**  
  Periods of **general inactivity** where the user does not perform any interaction (no clicks, no scrolling) for a noticeable duration.

- **Interpretation:**

  - Short inactivity → Normal thinking pause

  - Long inactivity → Possible confusion, overload, or indecision

## **Signal Mapping to Cognitive Load**

| **Signal**      | **Behavior Observed** | **Meaning**                 | **Cognitive Load Level** |
|-----------------|-----------------------|-----------------------------|--------------------------|
| Click Delay     | Very short            | Confident action            | Low                      |
| Click Delay     | Long delay            | Hesitation                  | Medium / High            |
| Scroll Behavior | Fast scroll           | Skimming / low engagement   | Low                      |
| Scroll Behavior | Slow + pauses         | Careful reading / confusion | High                     |
| Scroll Behavior | Erratic (up/down)     | Uncertainty                 | High                     |
| Backtracking    | Frequent              | Difficulty deciding         | High                     |
| Errors          | Repeated mis-clicks   | Confusion                   | High                     |
| Hesitation      | Long inactivity       | Overthinking / overload     | High                     |
| Hesitation      | Short pause           | Normal decision-making      | Low / Medium             |

## **Signal Categories (Important for clarity)**

### **🔹 Engagement Signals**

- Scroll speed

- Time on page

### **🔹 Confusion Signals**

- Repeated clicks

- Backtracking

- Misclicks

### **🔹 Cognitive Effort Signals**

- Click delay

- Hesitation time

## **How Signals Are Used in the System**

1.  Signals are captured in the **Tracking Layer**

2.  Each signal is converted into a **numeric value**

3.  Values are sent to the **Cognitive Load Engine**

4.  Combined into a **Cognitive Load Score**

5.  Used to classify:

    a.  Low

    b.  Medium

    c.  High

## **Example Scenario**

- User scrolls slowly + pauses frequently

- Takes long time before clicking

- Clicks wrong product twice

System interprets:

- High hesitation

- High confusion

- High cognitive effort

**Result: HIGH Cognitive Load**  
UI Adapter simplifies the interface

## **Future Enhancements**

- Add mouse movement tracking

- Machine learning-based signal weighting

- Personalization based on past behavior
