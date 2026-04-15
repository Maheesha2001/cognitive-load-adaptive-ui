***MVP Plan***


### **1. Overview**

The MVP focuses on building a **working prototype** of a Cognitive Load Adaptive Interface system.

The prototype demonstrates three core capabilities:

- User behavior tracking via browser interactions

- Cognitive load estimation using a rule-based scoring model

- Real-time UI adaptation based on cognitive load level

The goal is to validate the concept using a **minimal but functional system**, not a production-ready product.

### **2. MVP Features**

#### **Core Features**

- A simulated e-commerce product page (Daraz-like interface)

- Real-time user interaction tracking

- Rule-based cognitive load calculation

- Live display of cognitive load state

- Basic UI adaptation based on load level

### **3. System Architecture (MVP Scope)**

The MVP follows a simplified pipeline:

**User → Demo UI → Tracking Layer → Load Scoring Engine → UI Adapter → Updated UI**

All components run on the **client side (JavaScript-based MVP)**.

### **4. Step-by-Step Implementation Plan**

#### **Step 1: Build Demo UI (Frontend Layer)**

**Objective:** Create a realistic but simple e-commerce interface.

#### **Tasks:**

- Build product listing page

- Create product cards with:

  - Image

  - Title

  - Price

  - "Add to Cart" button

- Add simple filters (category, price)

- Enable scrolling interaction

#### **Output:**

✔ Functional static e-commerce UI (simulation environment)

##### **Suggested Tech:**

- HTML

- CSS

- JavaScript

#### **Step 2: Implement Tracking Layer (Behavior Capture)**

**Objective:** Capture user interaction signals.

##### **Tracked Signals:**

- Click delay (time before clicking an element)

- Scroll behavior (speed and direction changes)

- Hesitation (inactivity between interactions)

- Backtracking (revisiting previous UI elements)

- Interaction corrections (multiple selections before final choice)

##### **Implementation:**

Use JavaScript event listeners:

- click

- scroll

- mousemove (optional future use)

##### **Output:**

✔ Real-time behavioral data stream

#### **Step 3: Cognitive Load Engine (Scoring System)**

**Objective:** Convert behavioral signals into a cognitive load score.

##### **Tasks:**

- Implement rule-based scoring formula

- Normalize input signals

- Compute real-time cognitive load score

- Classify into:

  - Low (0--30)

  - Medium (31--60)

  - High (61+)

##### **Output:**

✔ Live cognitive load classification system

##### **Display:**

- "Cognitive Load: LOW"

- "Cognitive Load: MEDIUM"

- "Cognitive Load: HIGH"

#### **Step 4: UI Adaptation Layer**

**Objective:** Modify interface based on cognitive load level.

##### **LOW LOAD (0--30)**

- Show full product catalog

- Display all filters and navigation

- No UI modifications

##### **MEDIUM LOAD (31--60)**

- Highlight recommended products

- Reduce visual noise (dim secondary elements)

- Show subtle hints ("Recommended for you")

##### **HIGH LOAD (61+)**

- Reduce visible products (top 3--5 only)

- Hide advanced filters

- Increase spacing for clarity

- Show guidance messages

- Emphasize primary action buttons

##### **Implementation:**

- DOM manipulation (JavaScript)

- CSS class toggling

- Conditional rendering

### **5. User Flow (MVP)**

1.  User opens demo product page

2.  User scrolls and interacts

3.  Tracking layer collects behavioral signals

4.  Cognitive Load Engine calculates score

5.  System displays load level

6.  UI adapts dynamically

### **6. Technology Stack**

| **Component**  | **Technology**             |
|----------------|----------------------------|
| Frontend UI    | HTML, CSS, JavaScript      |
| Tracking Layer | JavaScript Event Listeners |
| Logic Engine   | JavaScript (rule-based)    |
| Hosting        | Localhost / GitHub Pages   |

### **7. Success Criteria**

The MVP is successful if:

- User interactions are correctly captured

- Cognitive load updates in real time

- Load classification works consistently

- UI changes reflect load state

- System runs smoothly without performance issues

### **8. Risks & Challenges**

- Inaccurate behavioral signal interpretation

- Improper threshold tuning (0--30 / 31--60 / 61+)

- UI changes may feel abrupt if not smooth

- Browser event noise (scroll/click sensitivity issues)

### **9. Future Improvements (Post-MVP)**

- Machine learning-based cognitive load prediction

- Personalized adaptation based on user history

- Mobile optimization

- Backend integration for data logging

- Advanced behavioral signals (mouse patterns, dwell time heatmaps)
