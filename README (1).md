# 🚴 AdventureWorks Cycles – Power BI Business Intelligence Report

> Profesjonalny raport BI zbudowany w Power BI Desktop w ramach kursu **Microsoft Power BI Desktop for Business Intelligence** (Maven Analytics / Udemy).

---

## 📸 Screenshots

> 💡 **Jak dodać screeny – instrukcja poniżej README**

### Exec Summary – KPI Overview
<!--
  JAK DODAĆ SCREEN:
  1. W Power BI Desktop naciśnij Win + Shift + S
  2. Zaznacz obszar dashboardu
  3. Zapisz jako PNG w folderze /screenshots
  4. Wgraj na GitHub i usuń ten komentarz
-->
![Exec Summary](screenshots/01_exec_summary.png)

### Regional Performance Map
![Regional Map](screenshots/02_regional_map.png)

### Product Detail
![Product Detail](screenshots/03_product_detail.png)

### Customer Detail
![Customer Detail](screenshots/04_customer_detail.png)

---

## 📋 Project Overview

| | |
|---|---|
| **Tool** | Microsoft Power BI Desktop |
| **Course** | [Microsoft Power BI Desktop for Business Intelligence – Maven Analytics (Udemy)](https://www.udemy.com/course/microsoft-power-bi-up-running-with-power-bi-desktop/) |
| **Instructor** | Chris Dutton – Maven Analytics |
| **Dataset** | AdventureWorks Cycles (provided in course) |
| **Domain** | Sales / Manufacturing / Business Intelligence |
| **Type** | Descriptive Analytics / KPI Dashboard |

---

## 🎯 Business Context

Wcielam się w rolę **Business Intelligence Analyst** dla AdventureWorks Cycles – fikcyjnego producenta rowerów.

**Cele raportu:**
- Śledzenie kluczowych wskaźników wydajności (KPIs)
- Porównanie wyników sprzedaży według regionów
- Analiza trendów na poziomie produktów
- Identyfikacja najbardziej wartościowych klientów

---

## 📊 Report Pages

### 1. 📈 Exec Summary
- KPI Cards: Revenue, Profit, Orders, Return Rate
- Revenue trending line chart (monthly)
- Orders by Category (bar chart)
- Top 10 Products table (orders, revenue, return rate)
- Slicer: Date range

### 2. 🗺️ Regional Performance
- Map visual: Orders by region (bubble map)
- Slicer: Continent filter
- Revenue by country comparison

### 3. 🛍️ Product Detail
- Gauge charts: Monthly Orders vs Target, Revenue vs Target, Profit vs Target
- Price adjustment parameter (what-if analysis)
- Profit vs Adjusted Profit line chart
- Metric selector slicer

### 4. 👤 Customer Detail
- Total customers & revenue per customer KPIs
- Line chart: Customers over time
- Donut charts: Orders by Income Level, Orders by Occupation
- Top 100 Customers table

---

## 🔢 Key DAX Measures

```dax
-- Total Revenue
Total Revenue =
SUMX(
    Sales_Data,
    Sales_Data[OrderQuantity] * RELATED(Product_Lookup[ProductPrice])
)

-- Total Profit
Total Profit =
[Total Revenue] - [Total Cost]

-- Return Rate
Return Rate =
DIVIDE(
    [Total Returns],
    [Total Orders],
    0
)

-- Revenue Target (poprzedni miesiąc +10%)
Revenue Target =
[Previous Month Revenue] * 1.10

-- YTD Revenue
YTD Revenue =
CALCULATE(
    [Total Revenue],
    DATESYTD('Calendar_Lookup'[Date])
)

-- 90-day Rolling Revenue
90-Day Rolling Revenue =
CALCULATE(
    [Total Revenue],
    DATESINPERIOD(
        'Calendar_Lookup'[Date],
        LASTDATE('Calendar_Lookup'[Date]),
        -90,
        DAY
    )
)
```

---

## 🗄️ Data Model

```
Calendar_Lookup ──────────────────────────────┐
(Date, Year, Month, Quarter, Weekend, etc.)   │
                                               │
Customer_Lookup ──────────────────────────────┤
(CustomerKey, Name, Income Level, Occupation) │
                                               │ *
Product_Lookup ──────────────────────────────► Sales_Data ◄── Returns_Data
(ProductKey, Name, Price, Cost)               │
       │                                       │
Product_Subcategories ────────────────────────┘
       │
Product_Categories
```

**Model type:** Star Schema  
**Relationships:** One-to-many, Single filter direction

---

## 🧹 Data Preparation (Power Query)

- [x] Connected to CSV source files
- [x] Promoted headers
- [x] Changed data types (dates, numbers, text)
- [x] Added conditional columns (e.g. SKU Type)
- [x] Replaced null/zero values
- [x] Merged queries (Product Subcategories → Categories)
- [x] Built Calendar table with DAX
- [x] Disabled auto date/time and auto relationships

---

## ✨ Key Features Implemented

| Feature | Description |
|---|---|
| **What-If Parameter** | Price adjustment slider affecting profit calculations |
| **Bookmarks** | Slicer panel show/hide toggle |
| **Drillthrough** | Product detail page accessible from summary |
| **Custom Tooltips** | Hover over visuals for additional context |
| **Dynamic Titles** | Titles update based on selected filters |
| **Conditional Formatting** | Color scales on KPI tables |
| **AI Visuals** | Decomposition Tree, Key Influencers |
| **Q&A Visual** | Natural language query interface |
| **Report Navigation** | Custom buttons between pages |

---

## 🛠️ Skills Demonstrated

`Power BI Desktop` `Power Query (M)` `DAX` `Data Modeling` `Star Schema` `Time Intelligence` `What-If Parameters` `Bookmarks` `Drillthrough` `Custom Tooltips` `Report Design` `KPI Dashboards` `Data Visualization`

---

## 📁 Repository Structure

```
📦 powerbi-adventureworks
 ┣ 📂 screenshots
 ┃ ┣ 🖼️ 01_exec_summary.png
 ┃ ┣ 🖼️ 02_regional_map.png
 ┃ ┣ 🖼️ 03_product_detail.png
 ┃ ┗ 🖼️ 04_customer_detail.png
 ┣ 📊 AdventureWorks_Report.pbix
 ┗ 📄 README.md
```

---

## 🚀 How to Open

1. Pobierz plik `AdventureWorks_Report.pbix`
2. Otwórz w **Power BI Desktop** (bezpłatny download od Microsoft)
3. Dane są wbudowane w plik – raport działa od razu po otwarciu

---

## 📚 Course Reference

Projekt zrealizowany w ramach kursu:

**[Microsoft Power BI Desktop for Business Intelligence](https://www.udemy.com/course/microsoft-power-bi-up-running-with-power-bi-desktop/)**  
Maven Analytics | Chris Dutton | ⭐ #1 Best Seller on Udemy

---

## 👤 Author

**[Twoje Imię i Nazwisko]**  
[LinkedIn](https://linkedin.com/in/twoj-profil) · [GitHub](https://github.com/twoj-profil)
