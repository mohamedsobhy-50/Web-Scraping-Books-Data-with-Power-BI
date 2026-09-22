# 📚 Books Analytics – Web Scraping & Dashboard with Power BI

> An end-to-end data analytics workflow: web scraping → cleaning → DAX analysis → interactive dashboard

**Developed by:** Mohamed Alkazaz  
**Contact:** [📧 mohamedsophy56665@gmail.com](mailto:mohamedsophy56665@gmail.com) | [🔗 LinkedIn](https://www.linkedin.com/in/mohammed-el-kazaz/)

---

## 🎯 Project Overview

This project demonstrates a **complete data analytics pipeline** using Power BI and Power Query to extract, clean, analyze, and visualize book e-commerce data.

### Key Deliverables
- ✅ Web scraping automation using Power Query
- ✅ Data cleaning & validation pipeline
- ✅ DAX calculations for business intelligence
- ✅ Interactive Power BI dashboard with filters and KPIs

![Dashboard Preview](dashboard%20project.png)

## 📊 Dataset Specifications

| Metric | Value |
|--------|-------|
| **Data Source** | [Books to Scrape](https://books.toscrape.com/) |
| **Total Records** | 1,000 books |
| **Pages Scraped** | 50 pages (20 books/page) |
| **Primary Fields** | Title, Price, URL, Page |
| **Data Quality** | 0 missing values, 0 errors, 0 duplicates |

---

## 🔄 Project Workflow

### 1️⃣ **Web Scraping** 🌐
- **Tool:** Power Query (Custom Function for pagination)
- **Extraction:** Dynamic data retrieval from dynamic HTML tables
- **Method:** HTTP requests + iterative page crawling
- **Output:** Raw dataset with 1,000 records

```
Loop through pages 1–50
  → Extract book title, price, availability
  → Append to consolidated dataset
```

### 2️⃣ **Data Cleaning & Exploration** 🧹

#### Transformations Applied
| Step | Action | Impact |
|------|--------|--------|
| Column Rename | Standardized naming conventions | Improved readability |
| Data Type Conversion | Price: Text → Decimal (Currency) | Enables calculations |
| Symbol Removal | Removed `£` prefix from prices | Clean numerical values |
| Text Cleaning | Applied Trim & Clean to titles | Removed extra spaces |
| Validation Checks | Identified missing/error values | Ensured data integrity |
| Duplicate Detection | Investigated via URL matching | Confirmed unique records |
| Feature Removal | Dropped `Availability` field | Single-value column (unused) |

**Quality Metrics:**
- ✅ 1,000 valid records
- ✅ 0 missing values
- ✅ 0 data errors
- ✅ 0 duplicates

### 3️⃣ **DAX Analysis** 📐

Core measures and calculations:

```DAX
-- Aggregate Metrics
Total Books = COUNTROWS('All Pages')
Average Price = AVERAGE('All Pages'[Price])
Minimum Price = MIN('All Pages'[Price])
Maximum Price = MAX('All Pages'[Price])
Price Range = [Maximum Price] - [Minimum Price]
Total Pages = DISTINCTCOUNT('All Pages'[Page])

-- Price Segmentation
Price Category = 
    IF([Price] < 20, "Low", 
        IF([Price] < 40, "Medium", "High"))
```

**Price Tiers:**
- 🟢 **Low:** £0–£19.99
- 🟡 **Medium:** £20–£39.99
- 🔴 **High:** ≥£40

### 4️⃣ **Interactive Dashboard** 📈

#### Dashboard Components

**Key Performance Indicators (KPIs)**
- Total Books Count
- Average Price (Mean)
- Min/Max Price Range
- Price Range Spread

**Visualizations**
- 📊 **Price Distribution Chart** – Histogram showing pricing patterns
- 🏆 **Top 10 Most Expensive Books** – Bar chart with titles and prices
- 💰 **Top 10 Cheapest Books** – Budget-friendly options
- 🏷️ **Price Category Breakdown** – Pie chart (Low/Medium/High split)
- 🎛️ **Interactive Slicers** – Filter by price range, category

**Features**
- Cross-filtering across all visuals
- Responsive design for desktop/mobile
- Export-ready reports

---

## 🛠️ Technologies & Tools

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Data Extraction** | Power Query (M Language) | Web scraping + pagination |
| **Data Transformation** | Power Query | Cleaning, validation, enrichment |
| **Analysis Engine** | DAX (Data Analysis Expressions) | KPI calculations, measures |
| **Visualization** | Power BI Desktop | Dashboard & interactive reports |

---

## 📈 Key Insights

- **Total Books Analyzed:** 1,000
- **Price Distribution:** Multimodal with concentration in Medium tier
- **Average Price:** [Display from your dashboard]
- **Price Variance:** [High/Medium/Low ratio]
- **Most Common Category:** [Based on tier analysis]

---

## 🚀 Getting Started

### Prerequisites
- Microsoft Power BI Desktop (latest version)
- Internet connection (for web scraping)
- Basic knowledge of Power Query & DAX

### Installation

1. **Clone or download** this repository
   ```bash
   git clone https://github.com/MohamedAlkazaz/books-analytics-powerbi.git
   cd books-analytics-powerbi
   ```

2. **Open the Power BI file**
   - Launch `Books_Analytics_Dashboard.pbix` in Power BI Desktop

3. **Refresh data** (if scraping again)
   - Home → Refresh / Transform Data → Edit Queries
   - Modify source URL if needed
   - Click Apply & Close

4. **Explore the dashboard**
   - Use slicers to filter by price range
   - Hover over visuals for tooltips
   - Export reports as needed

---

## 📋 File Structure

```
books-analytics-powerbi/
├── README.md                          # This file
├── Books_Analytics_Dashboard.pbix     # Power BI workbook
├── Data/
│   ├── books_raw.csv                 # Raw scraped data (optional)
│   └── books_cleaned.csv             # Processed dataset (optional)
└── Documentation/
    ├── DAX_Formulas.md               # Complete DAX reference
    └── Data_Dictionary.md            # Column definitions
```

---

## 🔮 Future Enhancements

### Phase 2 Features
- [ ] Add **Category, Rating, UPC, Tax, Description** fields
- [ ] Analyze **Price vs Rating** correlation
- [ ] Segment analysis by **book category**
- [ ] Statistical outlier detection
- [ ] **Scheduled data refresh** (automatic updates)

### Phase 3 (Advanced)
- [ ] Star Schema model design
- [ ] Machine Learning integration (price prediction)
- [ ] Time-series forecasting
- [ ] Sentiment analysis (customer reviews)
- [ ] Cloud deployment (Power BI Service)

---

## 📊 Sample Metrics

| Metric | Formula | Use Case |
|--------|---------|----------|
| Books by Tier | CALCULATE(COUNTA(), Category) | Inventory segmentation |
| Avg Price by Category | AVERAGEX(Category, Price) | Pricing strategy |
| Price Elasticity | (Max-Min)/Avg | Market analysis |
| Top Sellers | TOPN(10, Books, Price DESC) | Best performers |

---

## 🎓 Learning Outcomes

This project teaches:
- ✅ Web scraping techniques using Power Query
- ✅ Data cleaning best practices
- ✅ DAX for advanced analytics
- ✅ Dashboard design principles
- ✅ Interactive storytelling with data
- ✅ Business intelligence workflows

---

## 📝 License

This project is open source and available under the **MIT License**.

---

## 🤝 Contributing

Found a bug? Have an enhancement idea?

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

---

## 📞 Support & Contact

**Questions or feedback?**

📧 **Email:** [mohamedsophy56665@gmail.com](mailto:mohamedsophy56665@gmail.com)  
🔗 **LinkedIn:** [Mohammed El Kazaz](https://www.linkedin.com/in/mohammed-el-kazaz/)  

---

## 📚 Resources & References

- [Power Query Documentation](https://learn.microsoft.com/en-us/power-query/)
- [DAX Reference](https://learn.microsoft.com/en-us/dax/)
- [Power BI Best Practices](https://learn.microsoft.com/en-us/power-bi/)
- [Books to Scrape](https://books.toscrape.com/) – Dataset source

---

**⭐ If this project helped you, please star the repository!**

**Last Updated:** September 2026  
**Status:** Active & Maintained
