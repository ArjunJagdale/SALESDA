# Sales Data Analysis - Complete Documentation

## 📋 Project Overview

This project performs comprehensive analysis on sales data containing 1,194 orders across multiple categories, states, and time periods. The analysis leverages Python's data science stack to extract meaningful insights from transaction data spanning 2020-2025.

---

## 🛠️ Technology Stack & Role of Each Module

### **1. NumPy (Numerical Python)**
**Purpose:** High-performance numerical computations and statistical analysis

**Specific Functions Used:**
- `np.mean()` - Calculated average values for Amount, Profit, and Quantity
- `np.median()` - Found middle values in the distribution
- `np.std()` - Computed standard deviation to measure data spread
- `np.var()` - Calculated variance for understanding data variability
- `np.min()` / `np.max()` - Identified range boundaries
- `np.percentile()` - Determined 25th and 75th percentiles for quartile analysis
- `np.arange()` - Generated evenly spaced values for bar chart positioning

**Key Contributions:**
- Provided precise statistical metrics (mean: $5,178.09, median: $5,152.00)
- Enabled variance analysis (Amount variance: 7,860,997.91)
- Supported advanced mathematical operations for visualizations

---

### **2. Pandas (Panel Data)**
**Purpose:** Data manipulation, cleaning, and structured analysis

**Core Operations Performed:**

#### **Data Loading & Inspection**
- `pd.read_csv()` - Loaded 1,194 rows × 12 columns dataset
- `.head()` / `.tail()` - Previewed first and last records
- `.info()` - Displayed data types and memory usage (112.1+ KB)
- `.describe()` - Generated statistical summaries for numerical columns

#### **Data Cleaning & Transformation**
- `pd.to_datetime()` - Converted Order Date strings to datetime objects
- `.dt.year`, `.dt.month`, `.dt.quarter`, `.dt.day_name()` - Extracted temporal features
- `.str.strip()` - Removed whitespace from 9 object-type columns
- `.isnull().sum()` - Verified zero missing values
- `.duplicated().sum()` - Confirmed zero duplicate records

#### **Aggregation & GroupBy Analysis**
- `.groupby()` - Performed multi-dimensional aggregations:
  - By Category: Total Amount ($2.09M), Profit ($551K), Quantity (4,046)
  - By Payment Mode: 5 modes analyzed (Debit Card: $1.39M, 260 orders)
  - By Year-Month: 61 time periods tracked
  - By State: 6 states analyzed (New York: $1.13M)
  - By Customer: Top 10 customers identified (Cory Evans: $28,557)

- `.agg()` - Applied multiple aggregation functions simultaneously:
  ```python
  ['sum', 'mean', 'count']  # For payment mode analysis
  ```

#### **Time Series Analysis**
- Created yearly performance metrics showing:
  - 2022 peak revenue: $1.46M (+23.56% YoY growth)
  - 2023-2024 decline: -15.76% and -2.22% respectively
  - Monthly trend analysis across 61 periods

#### **Feature Engineering**
- Calculated Profit Margin % = (Profit / Amount) × 100
- Average margin: 26.06%
- Category margins: Office Supplies (26.40%), Furniture (26.51%), Electronics (25.24%)

---

### **3. Matplotlib**
**Purpose:** Core visualization library for static, publication-quality plots

**Visualization Components Created:**

#### **Figure Structure**
- `plt.figure(figsize=(20, 24))` - Created large multi-panel dashboard
- `plt.subplot(4, 3, n)` - Arranged 12 subplots in 4×3 grid
- `plt.tight_layout()` - Auto-adjusted spacing to prevent overlap
- `plt.savefig()` - Exported high-resolution images (300 DPI)

#### **Chart Types Implemented**

**1. Bar Charts** (Axes: ax1, ax2, ax3, ax11)
- Vertical bars for category comparisons (Amount, Profit, Profit Margin %)
- Grouped bars for yearly Revenue vs Profit comparison
- Color schemes: 'steelblue', 'green', 'coral'

**2. Horizontal Bar Charts** (Axes: ax5, ax10)
- Top 10 Sub-Categories by Revenue
- Top 10 States by Revenue
- Colors: 'purple', 'teal'

**3. Pie Chart** (Axis: ax4)
- Payment Mode Distribution with percentages
- Custom color palette from `plt.cm.Set3`

**4. Line Plots** (Axes: ax6, ax12)
- Monthly Sales Trend (61 data points)
- Quarterly Sales Trend
- Markers: 'o' (circles), 's' (squares)
- Line width: 2, Marker size: 6-8

**5. Histograms** (Axes: ax7, ax8, ax9)
- Distribution of Quantity (30 bins)
- Distribution of Amount (30 bins)
- Distribution of Profit (30 bins)
- Colors: 'skyblue', 'lightgreen', 'salmon'
- Alpha transparency: 0.7

#### **Styling & Customization**
- `plt.style.use('seaborn-v0_8-darkgrid')` - Applied consistent theme
- Grid alpha: 0.3 for subtle background
- Font sizes: Title (14, bold), Labels (default)
- Rotation: 45° for x-axis labels
- Edge colors: 'black' for histogram bars

---

### **4. Seaborn**
**Purpose:** Statistical data visualization with enhanced aesthetics

**Specific Applications:**

#### **Color Palettes**
- `sns.set_palette("husl")` - Applied perceptually uniform color scheme for all plots

#### **Correlation Heatmap**
- `sns.heatmap()` - Created correlation matrix visualization
  - Annotated with correlation coefficients (3 decimal places)
  - Colormap: 'coolwarm' (blue for negative, red for positive)
  - Center: 0 for diverging color scale
  - Square cells with 1px linewidth
  - Colorbar shrink: 0.8 for compact display

**Key Correlation Insights Visualized:**
- Amount ↔ Profit: 0.675 (strong positive)
- Profit ↔ Profit Margin %: 0.654 (strong positive)
- Amount ↔ Profit Margin %: -0.001 (no correlation)
- Quantity relationships: weak correlations (0.024-0.066)

---

## 📊 Analysis Results Summary

### **Business Metrics**
- **Total Revenue:** $6,182,639.00
- **Total Profit:** $1,610,697.00
- **Total Orders:** 547 unique Order IDs
- **Average Order Value:** $5,178.09
- **Overall Profit Margin:** 26.05%

### **Top Performers**
- **Best Category:** Office Supplies ($2,089,510 revenue)
- **Most Profitable Category:** Office Supplies ($551,575 profit)
- **Top State:** New York ($1,130,048 revenue, 226 orders)
- **Most Used Payment Mode:** Debit Card (260 orders, $1,395,035)
- **Best Month:** December 2022 ($204,413)

### **Trends Identified**
- **Peak Performance:** 2022 with $1.46M revenue (+23.56% YoY)
- **Decline Phase:** 2023-2024 showing -15.76% and -2.22% decline
- **Average Monthly Sales:** $101,354.74
- **Quarterly Pattern:** Tracked across 4 quarters per year

### **Statistical Insights**
- **Amount Distribution:** Mean $5,178, Median $5,152, Std Dev $2,804
- **Profit Distribution:** Mean $1,349, Range $50-$4,930
- **Quantity Distribution:** Mean 10.67, Range 1-20 units
- **Strong Correlation:** Amount and Profit (r=0.675)

---

## 📁 Output Files Generated

1. **sales_analysis_dashboard.png** (20×24 inches, 300 DPI)
   - 12-panel visualization dashboard
   - Category, payment, geographic, and temporal analyses

2. **correlation_matrix.png** (10×8 inches, 300 DPI)
   - Heatmap showing relationships between numerical variables
   - Color-coded correlation coefficients

---

## 🚀 How to Run

```bash
# Install required libraries
pip install numpy pandas matplotlib seaborn

# Run the notebook
jupyter notebook sales_analysis.ipynb

# Or run as Python script
python sales_analysis.py
```

**Prerequisites:**
- Python 3.7+
- CSV file with 12 columns (Order ID, Amount, Profit, Quantity, Category, Sub-Category, PaymentMode, Order Date, CustomerName, State, City, Year-Month)

---

## 📈 Key Findings

### **1. Category Performance**
- All three categories (Furniture, Office Supplies, Electronics) generate similar revenue (~$2M each)
- Office Supplies leads in both revenue and profit
- Profit margins are consistent across categories (25-26.5%)

### **2. Geographic Distribution**
- New York dominates with $1.13M revenue (18.3% of total)
- Top 6 states account for 100% of revenue
- Buffalo is the highest-performing city (90 orders)

### **3. Payment Preferences**
- Debit Card most popular (260 orders, 21.8%)
- Relatively even distribution across 5 payment modes
- COD has highest average order value ($5,542.67)

### **4. Temporal Patterns**
- Business peaked in 2022
- Experiencing gradual decline since 2023
- Monthly sales vary significantly ($52K-$204K range)
- December 2022 was the best-performing month

### **5. Customer Behavior**
- Top customer (Cory Evans) contributed $28,557
- Average quantity per order: 10.67 units
- Order sizes range from 1 to 20 units

---

## 🔍 Technical Highlights

### **Data Quality**
- ✅ Zero missing values across all 12 columns
- ✅ Zero duplicate records
- ✅ Clean datetime conversion with no errors
- ✅ Consistent data types post-preprocessing

### **Performance**
- Memory usage: 112.1+ KB (efficient)
- Processing time: Sub-second for 1,194 records
- High-resolution outputs: 300 DPI publication quality

### **Code Quality**
- Modular section-based structure (9 sections)
- Comprehensive error handling with warnings suppression
- Reusable functions and consistent naming conventions
- Detailed comments for each analysis step

---

## 📚 Libraries Version Compatibility

- **NumPy:** 1.x+ (tested with latest stable)
- **Pandas:** 1.3.0+ (datetime64[ns] support required)
- **Matplotlib:** 3.3.0+ (subplot and style features)
- **Seaborn:** 0.11.0+ (heatmap enhancements)

---

## 👨‍💻 Author Notes

This analysis demonstrates the power of Python's data science ecosystem:
- **NumPy** provides the mathematical foundation
- **Pandas** handles data manipulation and aggregation
- **Matplotlib** creates the visual framework
- **Seaborn** adds statistical aesthetics

Each library plays a complementary role, resulting in a comprehensive analytical workflow that transforms raw CSV data into actionable business insights.

---

## 📝 License

This analysis notebook is provided as-is for educational and analytical purposes.

---

**Last Updated:** January 2026  
**Dataset Period:** March 2020 - March 2025  
**Total Records Analyzed:** 1,194 orders
