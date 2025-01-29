A **unit hydrograph** represents the direct runoff response of a watershed to a unit depth of excess rainfall (typically 1 cm or 1 inch) occurring uniformly over the watershed for a specific duration (e.g., 1 hour). The shape of the unit hydrograph depends on:
- Watershed characteristics (area, slope, land use, soil type).
- Rainfall intensity and duration.
- Time of concentration (\(T_c\)): The time it takes for water to travel from the farthest point in the watershed to the outlet.
- Base time (\(T_b\)): The total duration of the direct runoff hydrograph.

---

### **2. Assumptions for Mukono**
- **Watershed area (\(A\))**: \(A = 128.6 \, \text{km}^2\) 
- **Rainfall duration (\(D\))**: 1 hour
- **Time of concentration (\(T_c\))**: Estimated using empirical formulas.
- **Peak discharge (\(Q_p\))**: Calculated using the rational method or synthetic unit hydrograph formulas.
- **Base time (\(T_b\))**: Typically \(2.67 \times T_c\) for a triangular unit hydrograph.

---

### **3. Equations and Calculations**

#### **Step 1: Estimate Time of Concentration (\(T_c\))**
The time of concentration (\(T_c\)) can be estimated using empirical formulas. For small watersheds, the **Kirpich equation** is commonly used:

\[
T_c = 0.0195 \cdot L^{0.77} \cdot S^{-0.385}
\]

Where:
- \(L\) = Length of the longest flow path (km). Assume \(L = 10 \, \text{km}\).
- \(S\) = Average watershed slope (m/m). Assume \(S = 0.02 \, \text{(2%)}\).

Substitute the values:
\[
T_c = 0.0195 \cdot (10)^{0.77} \cdot (0.02)^{-0.385}
\]
\[
T_c \approx 4 \, \text{hours}
\]

---

#### **Step 2: Estimate Base Time (\(T_b\))**
For a triangular unit hydrograph, the base time (\(T_b\)) is approximately:
\[
T_b = 2.67 \cdot T_c
\]
\[
T_b = 2.67 \cdot 4 = 10.68 \, \text{hours} \approx 11 \, \text{hours}
\]

---

#### **Step 3: Calculate Peak Discharge (\(Q_p\))**
The peak discharge (\(Q_p\)) can be estimated using the **rational method** or **synthetic unit hydrograph formulas**. For a unit hydrograph, the peak discharge is given by:

\[
Q_p = \frac{2.08 \cdot A}{T_p}
\]

Where:
- \(A\) = Watershed area (\(128.6 \, \text{km}^2\)).
- \(T_p\) = Time to peak, which is approximately \(T_c + \frac{D}{2}\).
  - \(D\) = Rainfall duration (\(1 \, \text{hour}\)).
  - \(T_p = 4 + \frac{1}{2} = 4.5 \, \text{hours}\).

Substitute the values:
\[
Q_p = \frac{2.08 \cdot 128.6}{4.5}
\]
\[
Q_p \approx 46.2 \, \text{m}^3/\text{s} \approx 50 \, \text{m}^3/\text{s}
\]

---

#### **Step 4: Define the Unit Hydrograph Shape**
The unit hydrograph is typically represented as a triangular or gamma distribution. For simplicity, we’ll use a triangular shape with:
- Rising limb: From \(t = 0\) to \(t = T_p\) (4.5 hours).
- Falling limb: From \(t = T_p\) to \(t = T_b\) (11 hours).

The discharge at any time \(t\) can be calculated as:
- Rising limb: \(Q(t) = Q_p \cdot \frac{t}{T_p}\)
- Falling limb: \(Q(t) = Q_p \cdot \frac{T_b - t}{T_b - T_p}\)

---

#### **Step 5: Generate Discharge Values**
Using the equations above, we can calculate the discharge at hourly intervals:

| Time (hours) | Discharge (m³/s) Calculation                     | Discharge (m³/s) |
|--------------|--------------------------------------------------|------------------|
| 0            | \(Q(0) = 0\)                                     | 0                |
| 1            | \(Q(1) = 50 \cdot \frac{1}{4.5}\)                | 11.1             |
| 2            | \(Q(2) = 50 \cdot \frac{2}{4.5}\)                | 22.2             |
| 3            | \(Q(3) = 50 \cdot \frac{3}{4.5}\)                | 33.3             |
| 4            | \(Q(4) = 50 \cdot \frac{4}{4.5}\)                | 44.4             |
| 4.5          | \(Q(4.5) = 50\)                                  | 50               |
| 5            | \(Q(5) = 50 \cdot \frac{11 - 5}{11 - 4.5}\)      | 42.3             |
| 6            | \(Q(6) = 50 \cdot \frac{11 - 6}{11 - 4.5}\)      | 34.6             |
| 7            | \(Q(7) = 50 \cdot \frac{11 - 7}{11 - 4.5}\)      | 26.9             |
| 8            | \(Q(8) = 50 \cdot \frac{11 - 8}{11 - 4.5}\)      | 19.2             |
| 9            | \(Q(9) = 50 \cdot \frac{11 - 9}{11 - 4.5}\)      | 11.5             |
| 10           | \(Q(10) = 50 \cdot \frac{11 - 10}{11 - 4.5}\)    | 3.8              |
| 11           | \(Q(11) = 0\)                                    | 0                |

---

### **6. Final CSV Data**
The generated data can be saved as a CSV file:

```csv
Time (hours),Discharge (m³/s)
0,0
1,11.1
2,22.2
3,33.3
4,44.4
4.5,50
5,42.3
6,34.6
7,26.9
8,19.2
9,11.5
10,3.8
11,0
```
