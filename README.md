# 🚚 Corporate Carrier Performance & Optimization Scorecard

## 📌 Executive Summary
Developed an end-to-end data framework to evaluate, score, and optimize a cross-border bulk transportation network handling 1,000+ annual shipments across 5 strategic carrier partners. This interactive scorecard aggregates logistics performance to identify capacity risks, isolate root causes for transit delays, and enforce safety compliance across separate business units.

---

## 🎨 Interactive Dashboard Preview
Below is the live operational scorecard designed with an executive-level **Earthy Rose & Sage** palette to maximize scannability:

![Carrier Scorecard Dashboard](Images/your_screenshot_name.png)
*(Note: Replace "your_screenshot_name.png" with the exact name of the file you uploaded to your Images folder)*

---

## 🚀 Key Business Insights Uncovered
* **Service Bottlenecks Identified**: Carrier "C.H. Robinson" (CHRW) represents the highest network risk, dropping to an 83% On-Time Delivery rate driven primarily by preventable 'carrier delays' and 'equipment failures'.
* **Compliance Success**: Despite transit friction, the overall network maintains an excellent 95% Safety Compliance rating, hitting the corporate SLA target.
* **Volume Asymmetry**: Business Unit A commands 60% of total shipment volume, heavily skewing capacity demand during Q3 peak shipping windows.

---

## 📐 Data Architecture & Modeling
To demonstrate enterprise-grade design practices, the raw transactional logs were restructured from disjointed flat files into an optimized **Star Schema** inside Power BI. This architecture eliminates data duplication and ensures high-speed DAX measure performance.

### Core Data Model:
* **Fact Tables**: `Fact_Shipments` (Consolidated operational logs), `Fact_Safety` (Independent safety audits).
* **Dimension Tables**: `Dim_Vendor` (Carrier master data), `Dim_Shipment_Geo` (Geospatial attributes), `Dim_Regions` (Macro market territories).

---

## 💻 Featured Analytics Code

### Advanced Dynamic Carrier Ranking (DAX)
This measure bypasses inactive vendors and dynamically ranks active carrier partners based on cumulative composite scores, adjusting instantaneously to any active dashboard filters:

```dax
Carrier Rank = 
IF(
    NOT(ISBLANK([Composite Score])),
    RANKX(
        ALLSELECTED('Dim_Vendor'),
        [Composite Score],
        ,
        DESC,
        Dense
    )
)
```
