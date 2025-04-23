
# 🛍️ Amazon Sales Analysis 📊

This project dives into an in-depth analysis of Amazon's product sales using a real-world dataset. The goal is to uncover valuable insights around product categories, shipping patterns, customer behavior (B2B vs B2C), and more.

---

## 📁 Dataset

**Filename:** `Amazon Sale Report.csv`  
**Source:** Internal  
**Records:** Sales, shipping, customer, and product size information  
**Encoding Used:** `unicode_escape`

---

## 🧰 Libraries Used

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`

---

## 📌 Key Tasks & Steps

### ✅ Data Cleaning & Preprocessing

- Dropped irrelevant columns: `New`, `PendingS`
- Checked and removed all null values
- Converted:
  - `'ship-postal-code'` to `int`
  - `'Date'` to proper datetime format (`%m/%d/%Y`)

### 🧠 Data Exploration & Visualization

#### 🔹 Quantity Analysis by Size

```python
sns.countplot(x='Size', data=df)
```
- Most sold product size: **M (Medium)**

#### 🔹 Grouped Sales by Size (Total Quantity Sold)

```python
S_Qty = df.groupby(['Size'], as_index=False)['Qty'].sum().sort_values(by='Qty', ascending=False)
sns.barplot(x='Size', y='Qty', data=S_Qty)
```

#### 🔹 Courier Status vs Order Status

```python
sns.countplot(data=df, x='Courier Status', hue='Status')
```
- Understands delivery performance based on order outcome.

#### 🔹 Product Size Distribution

```python
df['Size'].hist()
```

#### 🔹 Category-Wise Purchase Histogram

```python
plt.hist(df['Category'], bins=30)
```
- **T-shirts** are the most demanded category.

#### 🔹 B2B vs B2C Sale Distribution

```python
plt.pie(df['B2B'].value_counts(), autopct='%1.1f%%')
```
- **99.2%** of sales are B2C; only **0.8%** are B2B.

#### 🔹 Category vs Size Scatter Plot

```python
plt.scatter(df['Category'], df['Size'])
```

#### 🔹 State-wise Distribution of Orders

```python
sns.countplot(data=df, x='ship-state')
```

#### 🔹 Top 10 States with Highest Sales

```python
top_10_states = df['ship-state'].value_counts().head(10)
sns.countplot(data=df[df['ship-state'].isin(top_10_states.index)], x='ship-state')
```
- 📌 **Maharashtra**, **Karnataka**, and **Tamil Nadu** are top performers.

---

## 📈 Key Insights

- **Size M** is the most popular size across categories.
- **T-Shirts** dominate the product category.
- Sales are **almost entirely B2C**, with minimal B2B transactions.
- Shipping performance can be visualized by courier and order status.
- **Maharashtra** has the highest order volume among Indian states.

---

## 💡 Future Improvements

- Deeper customer segmentation if demographic data is available.
- Predictive modeling for future demand forecasting.
- Integration with dashboards (e.g., Power BI, Tableau).

---

## 🤝 Contribution

Feel free to fork this repo and suggest improvements or contribute additional visualizations!

---

## 🧾 License

This project is under the [MIT License](LICENSE).
