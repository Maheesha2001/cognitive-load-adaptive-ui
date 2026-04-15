***System Architecture***

## **1. Architecture Overview**

The system follows a **layered architecture** that captures user
behavior, processes it to estimate cognitive load, and dynamically
adapts the user interface in real time.

The system is designed as a modular, real-time adaptive interface that
operates entirely on the client side for the MVP version.

### **High-Level Flow:**

**User → Frontend UI → Tracking Layer → Cognitive Load Engine → UI
Adapter → Updated UI**

## **2. System Components**

### **2.1 Frontend (UI Layer)**

A simulated **e-commerce product page (Daraz-like interface)** where all
user interactions occur.

#### **Responsibilities:**

-   Display product information (images, price, description)

-   Provide interactive elements:

    -   Add to cart

    -   Product selection

    -   Filters & sorting

-   Capture user interaction events (clicks, scrolls, navigation)

#### **Technologies (example):**

-   HTML, CSS, JavaScript

-   React / Angular (optional)

### **2.2 Tracking Layer (Browser Extension)**

-   A lightweight tracking module that monitors user interaction
    behavior in real time.

#### **Tracked Signals:**

-   **Click Delay** → Time taken before clicking an element

-   **Scroll Speed** → Fast/slow scrolling patterns

-   **Number of Interactions** → Click frequency

-   **Hesitation Time** → Idle time before action

#### **Additional Signals (Recommended Upgrade ⭐):**

-   Backtracking (revisiting pages)

-   Repeated clicks (confusion indicator)

#### **Responsibilities:**

-   Collect behavioral data

-   Preprocess signals

-   Send data to Cognitive Load Engine

### **2.3 Cognitive Load Engine**

The core logic unit that estimates the user\'s cognitive load level.

#### **Approach:**

Rule-based scoring system (MVP-friendly)

#### **Scoring Formula:**

Cognitive Load Score =

(Click Delay × 2)

\+ (Hesitation Time × 2)

\+ (Backtracking × 3)

\+ (Error Actions × 5)

\+ (Scroll Irregularity × 1)

#### **Load Classification:**

-   **Low Load** → Smooth interaction

-   **Medium Load** → Slight hesitation

-   **High Load** → Confusion / overload

#### **Responsibilities:**

-   Aggregate behavioral signals

-   Compute cognitive load score

-   Classify user state

-   Send output to UI Adapter

> Changes UI based on load:

-   simplify layout

-   reduce items

-   add hints

### **2.4 UI Adapter (Adaptive Interface Engine)**

Dynamically modifies the interface based on detected cognitive load.

#### **Adaptation Rules:**

##### **🔹 Low Load**

-   Show full interface

-   Enable all features

##### **🔹 Medium Load**

-   Highlight important elements

-   Reduce visual clutter slightly

-   Provide subtle hints

##### **🔹 High Load**

-   Simplify layout

-   Reduce number of visible items

-   Emphasize key actions (e.g., "Buy Now")

-   Show guidance (tooltips / suggestions)

#### **Responsibilities:**

-   Receive load classification

-   Apply UI transformation rules

-   Update UI in real time

## **3. Data Flow**

1.  User interacts with the **Frontend UI**

2.  **Tracking Layer** captures behavioral signals

3.  Data is sent to the **Cognitive Load Engine**

4.  Engine calculates load score and classification

5.  Result is sent to the **UI Adapter**

6.  UI is dynamically updated

7.  User experiences adapted interface

## **4. Technology Stack (Suggested)**

  -----------------------------------------------------------------------
  **Layer**                           **Technology**
  ----------------------------------- -----------------------------------
  Frontend                            HTML, CSS, JavaScript / React

  Tracking                            JavaScript (Event Listeners)

  Backend                             Not required for MVP

  Data Handling                       JSON

  Hosting                             Localhost / AWS (optional)
  -----------------------------------------------------------------------

## **5. Scalability Considerations**

-   Modular architecture (each component independent)

-   Can replace rule-based engine with ML model later

-   Cloud integration possible (AWS, Firebase)

-   Event streaming for real-time processing

## **6. Performance Considerations**

-   Lightweight tracking (avoid slowing UI)

-   Fast rule-based computation

-   Minimal DOM manipulation for UI updates

## **7. Security & Privacy Considerations**

-   Do not collect sensitive user data

-   Anonymize interaction data

-   Ensure transparency in tracking

## **8. Future Enhancements**

-   Machine Learning-based cognitive load detection

-   Personalization using user history

-   Cross-platform support (mobile apps)

-   Real-time analytics dashboard

-   Integration with real e-commerce platforms
