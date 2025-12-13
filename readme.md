## CISC 7201 FINAL PROJECT

## Usage Analysis and Recommendations for Sports Facilities at the University of Macau

### Overview
This project examines **usage patterns and optimization strategies for sports facilities at the University of Macau**. It focuses on three representative venues—**badminton, tennis, and squash**—and extends to a machine learning module that predicts **booking success rates**. The study covers data from **December 2022 to June 2024**, and it identifies clear temporal rules: **evening peaks**, **higher demand during teaching terms**, and **notable drops during exam periods**.

---

### Data collection
- **Data sources:** The official UM data platform (JSON), the **sport_facilities** code mapping, and the **UM Academic Calendar**. We scraped the API to build a venue mapping table so that codes (for example, the HBC series) match specific venue types.
- **Fields:** `bookingID`, `bookingDate`, `placeCode`, `timeSlot`, `bookingStatus`, `lastModifiedDate`. The letter codes in `bookingStatus` follow the definitions on the university website.

---

### Data preprocessing
- Converted original **JSON** files to **CSV**, unified field names and time zones, and merged multiple codes into single categories for the same type of venue.
- Explained `bookingStatus` and its distribution. We confirmed that **"available"** dominates, and some venues (especially basketball) use **offline registration** that is not synchronized to the online platform. Therefore, the core analysis focuses on **badminton, tennis, and squash**.
- Built a **daily time series**, filled missing dates using **forward fill**, and added labels for **seasons** and **teaching/holiday periods** to support visualization and modeling.

---

### Badminton court analysis
- Selected data using the **HBC** series (HBC1–HBC8, HBH, and related codes). We grouped `O/H/R` as **occupied statuses** to measure time ranges that are not open for new bookings.
- Time-series trends show **stable demand** throughout the year, with a clear rise in **August–October**. Median levels are similar between weekdays and weekends, but **Saturday and Sunday evenings** are more active.
- After aligning with the academic calendar, we find that **exam periods and winter breaks** show significant declines, while **summer** has a slight increase. As indoor sports, **badminton is more resistant to climate fluctuation**.

---

### Tennis court analysis
- **Fridays and Saturdays** have the highest and most variable usage; **Sundays** are lower. Usage rises in **February–April** (cooler spring weather) and drops in **June–September** due to summer heat. Tennis shows **strong seasonality** and high climate sensitivity.

---

### Squash court analysis
- Usage increases in **July–October**, while the **beginning of the year and holiday seasons** show declines. **Weekends and Fridays** are clearly more active, with wider ranges. Squash is less popular than badminton overall but has **concentrated weekend demand**.

---

### Machine learning
- **Task and features:** We predict booking success for four venue types (tennis, basketball, badminton, squash). Besides raw time fields, we design 18 interpretable features, including **weekend flag**, **time-of-day buckets** (morning 7:00–12:00, afternoon 13:00–17:00, evening 18:00–22:00), and **season markers** (summer: June–August; winter: December–February).
- **Models and results:** We compare **logistic regression** and **random forest**. Random forest reaches **79.42% accuracy** and **88% recall** on successful bookings, outperforming logistic regression (**74.48% accuracy**). Feature importance offers actionable insights for management.
- **Examples:** The model estimates **95.48%** booking success for basketball at **20:00 on Sunday**, and **38.75%** for badminton at **10:00 on Wednesday**. These predictions help users avoid peak times and improve booking decisions.
- **Management insights:** Weekdays show **67.21%** success, higher than weekends (**64.86%**). **16:00** is a campus **golden hour**. We suggest adjusting opening strategies or providing incentives during low-success periods. Future work will add **weather** and **course timetable** data and build an **interactive app** to increase practical value.

---

### Key findings & Recommendations
- **Usage patterns:** Evenings are most active; demand is highest in the **middle of teaching terms**; **holidays** show clear declines; **exam periods** are lowest and most stable. Indoor sports are more robust to climate changes, while outdoor sports vary more.
- **User advice:** Avoid **Friday/Saturday evenings** and mid-term peaks. Choose **weekday afternoons (e.g., 16:00)** or off-peak periods in spring/autumn to improve booking success.
- **Management advice:** During peak hours and mid-term, use **time-sliced booking** and **dynamic quotas**. Schedule **maintenance and training** in off seasons or exam periods. For outdoor sports in summer, add **shade and hydration facilities** and promote **staggered events**.

---

### Team & Credits
- **He Jingping:** 
- **Yao Jiahao:** 
- **Liang Zhengping:** 
- **Liang Zhongkai:** 
- **Zhang Yi:**

### References

