<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# 🛒 E-commerce Conversion Rate Analysis – Google Analytics 4

_Optimizing e-commerce conversion rates through comprehensive funnel analysis using BigQuery, Python, and data visualization to bridge the gap from 1.88% to 2.5% target conversion._

***

## 📌 Table of Contents

- <a href="#overview">Overview</a>
- <a href="#business-problem">Business Problem</a>
- <a href="#dataset">Dataset</a>
- <a href="#tools--technologies">Tools \& Technologies</a>
- <a href="#project-structure">Project Structure</a>
- <a href="#data-cleaning--preparation">Data Cleaning \& Preparation</a>
- <a href="#exploratory-data-analysis-eda">Exploratory Data Analysis (EDA)</a>
- <a href="#key-findings--insights">Key Findings \& Insights</a>
- <a href="#visualizations">Visualizations</a>
- <a href="#how-to-run-this-project">How to Run This Project</a>
- <a href="#strategic-recommendations">Strategic Recommendations</a>
- <a href="#author--contact">Author \& Contact</a>

***

<h2><a class="anchor" id="overview"></a>Overview</h2>

This project analyzes Google Analytics 4 e-commerce data to identify conversion optimization opportunities for an online merchandise store. Using BigQuery for data extraction and Python for comprehensive analysis, the study examines user behavior patterns, traffic source performance, and conversion funnels to achieve a target conversion rate improvement from 1.88% to 2.5%.

***

<h2><a class="anchor" id="business-problem"></a>Business Problem</h2>

The e-commerce store needs to improve conversion rates to maximize revenue from existing traffic. This analysis aims to:

- **Identify underperforming traffic sources** requiring optimization
- **Discover optimal timing patterns** for marketing campaigns
- **Analyze device-specific conversion behaviors** for UX improvements
- **Uncover geographic market opportunities** for targeted expansion
- **Map user journey patterns** to reduce conversion friction
- **Bridge the 0.62 percentage point gap** to reach 2.5% target conversion rate

***

<h2><a class="anchor" id="dataset"></a>Dataset</h2>

- **Source**: Google BigQuery public dataset (`bigquery-public-data.ga4_obfuscated_sample_ecommerce`)
- **Time Period**: November - December 2020
- **Records**: 2,151,546 total events
- **Key Events**: purchase, session_start, page_view, first_visit, user_engagement
- **Metrics**: 238,421 sessions resulting in 4,488 purchases (1.88% conversion rate)

***

<h2><a class="anchor" id="tools--technologies"></a>Tools \& Technologies</h2>

- **BigQuery**: Data extraction and initial processing
- **Python**: Data analysis and statistical testing
    - Pandas, NumPy for data manipulation
    - Matplotlib, Seaborn for statistical visualizations
    - Plotly for interactive charts and geographic mapping
- **Google Colab**: Development environment
- **GitHub**: Version control and project documentation

***

<h2><a class="anchor" id="project-structure"></a>Project Structure</h2>

```
ecommerce-conversion-analysis/
│
├── README.md
├── .gitignore
├── requirements.txt
│
├── notebooks/                          # Analysis notebooks
│   ├── Merchindising_google_analysis.ipynb
│   └── conversion_analysis_summary.ipynb
│
├── data/                              # Generated datasets
│   └── merchandise_store_full_data.csv
│
├── visualizations/                    # Generated charts
│   ├── traffic_source_conversion.png
│   ├── hourly_conversion_patterns.png
│   ├── device_performance.png
│   ├── geographic_heatmap.html
│   └── user_journey_sankey.html
│
└── sql/                              # BigQuery extraction queries
    └── ga4_data_extraction.sql
```


***

<h2><a class="anchor" id="data-cleaning--preparation"></a>Data Cleaning \& Preparation</h2>

- **Removed duplicate rows**: 0 duplicates found in dataset
- **Handled missing values**: Purchase-related fields naturally NULL for non-purchase events
- **Feature engineering**:
    - Created `is_purchase` binary indicator
    - Extracted `hour`, `day_name`, `is_weekend` from timestamps
    - Converted data types for optimal analysis
- **Data validation**: Identified 1,236 duplicate transaction IDs requiring investigation

***

<h2><a class="anchor" id="exploratory-data-analysis-eda"></a>Exploratory Data Analysis (EDA)</h2>

**Event Distribution Analysis:**

- Page Views: 931,424 events (43.3%)
- User Engagement: 808,624 events (37.6%)
- Session Starts: 238,421 events (11.1%)
- First Visits: 168,589 events (7.8%)
- Purchases: 4,488 events (0.2%)

**User Journey Patterns:**

- Total unique users: 179,058
- Converting users: 3,409 (1.9%)
- Non-converting users: 175,649 (98.1%)
- Average events per converting user: Much higher engagement before purchase

***

<h2><a class="anchor" id="key-findings--insights"></a>Key Findings \& Insights</h2>

### **1. Traffic Source Performance Crisis 🚨**

- **Google traffic**: 0.168% conversion (worst performer despite highest volume)
- **(data deleted) source**: 0.453% conversion (best performer)
- **Direct traffic**: 0.198% conversion
- **Opportunity**: Fixing Google traffic could yield +115 purchases from existing volume


### **2. Optimal Timing Patterns ⏰**

- **Peak conversion hours**: 5 AM (0.254%), 4 PM (0.249%), 10 PM (0.242%)
- **Weekday vs Weekend**: 0.217% vs 0.178% conversion
- **Action**: Shift ad spend to peak hours and focus on weekday campaigns


### **3. Device Performance Surprise ✅**

- **Mobile**: 0.216% conversion (outperforms desktop!)
- **Desktop**: 0.205% conversion
- **Tablet**: 0.176% conversion
- **Insight**: No mobile friction issues - leverage mobile advantage


### **4. Geographic Market Opportunities 🌍**

**High-volume, low-conversion markets:**

- **United States**: 0.205% conversion (960,227 events) - Major optimization opportunity

**High-converting smaller markets:**

- **Uruguay**: 0.570% conversion
- **Slovenia**: 0.501% conversion
- **Colombia**: 0.390% conversion

***

<h2><a class="anchor" id="visualizations"></a>Visualizations</h2>

The analysis includes comprehensive visualizations:

1. **Traffic Source Conversion Bar Chart** - Highlights Google's underperformance
2. **Hourly Conversion Heatmap** - Reveals peak conversion times
3. **Device Category Performance** - Shows mobile's competitive advantage
4. **Geographic Conversion Choropleth** - Maps global conversion opportunities
5. **User Journey Sankey Diagram** - Visualizes conversion flow patterns
6. **Day-Hour Conversion Heatmap** - Identifies optimal campaign timing

***

<h2><a class="anchor" id="how-to-run-this-project"></a>How to Run This Project</h2>

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/ecommerce-conversion-analysis.git
```

2. **Set up Google Cloud credentials:**
```python
from google.colab import auth
auth.authenticate_user()
```

3. **Install required packages:**
```bash
pip install pandas matplotlib seaborn plotly google-cloud-bigquery
```

4. **Run the BigQuery data extraction:**
```python
# Execute the SQL query in notebooks/Merchindising_google_analysis.ipynb
# This will create merchandise_store_full_data.csv
```

5. **Execute analysis notebooks:**
    - Open `notebooks/Merchindising_google_analysis.ipynb`
    - Run all cells to reproduce analysis and visualizations
6. **View interactive visualizations:**
    - Geographic heatmap: Open `visualizations/geographic_heatmap.html`
    - User journey flow: Open `visualizations/user_journey_sankey.html`

***

<h2><a class="anchor" id="strategic-recommendations"></a>Strategic Recommendations</h2>

### **Immediate Actions (0-30 days)**

- **Audit Google Ads campaigns** - investigate 0.168% conversion rate
- **Reallocate ad budget** to peak hours (5 AM, 4 PM, 10 PM)
- **Reduce weekend ad spend** in favor of weekday focus


### **Medium-term Optimizations (1-3 months)**

- **Leverage mobile advantage** in campaign creative and landing pages
- **Scale successful tactics** from high-converting countries to US market
- **A/B test checkout flow** improvements during peak hours


### **Long-term Strategic Initiatives (3-6 months)**

- **Implement dynamic bidding** based on hourly conversion patterns
- **Develop mobile-first user experience** optimization program
- **Create geographic targeting strategy** for high-converting markets


### **Expected Impact**

Achieving these optimizations could bridge the **0.62 percentage point gap** to reach the **2.5% target conversion rate**, representing approximately **1,474 additional purchases** from existing traffic volume.

***


**Yash Tyagi**
Data Analyst \& E-commerce Analytics Specialist
📧 Email: [tyagiyaxh627@gmail.com]
🔗 LinkedIn: [https://www.linkedin.com/in/yash-tyagi-9a38b1350/)
🐙 GitHub: [GitHub Profile](https://github.com/Yaxhfr7)

*Specializing in conversion rate optimization, user behavior analysis, and data-driven marketing strategies.*

