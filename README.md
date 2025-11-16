# Sales Data Cleaning Script

This project cleans and preprocesses a raw sales dataset (`unclean_sales_data_500.csv`) using **Python (pandas)**.
It fixes missing values, inconsistent text entries, incorrect data types, and invalid dates — preparing the dataset for reliable analysis.

---

## 🚀 Features

### **1. Missing Value Handling**

* Removes rows with missing critical fields (`category`, `state`, `delivery_method`, `order_date`).
* Converts `quantity` and `price` to numeric and fills missing values with their respective means.

### **2. Data Type Corrections**

* `quantity` → converted to integer.
* `price` → converted to float after coercing invalid entries.
* `order_date` → parsed into valid datetime objects.

### **3. Text Standardization**

* State names normalized:

  * `karnataka`, `KA` → `Karnataka`
  * `maharastra`, `MH` → `Maharastra`
* Delivery method normalized:

  * `cod` → `COD`
  * `online`, `Onlne` → `Online`

### **4. Invalid Data Removal**

* Drops rows with invalid or unparseable dates.
* Removes rows where key categorical values remain missing even after cleaning.

### **5. Output**

* Prints the fully cleaned DataFrame using `df.to_string()`.

---

## 🧠 Requirements

Install pandas (Python 3.8+ required):

```bash
pip install pandas
```

---

## ▶️ How to Run

Ensure the file `unclean_sales_data_500.csv` is in the same directory as the script.

Run the script:



---

## 📌 Notes

* The cleaning process is destructive — rows removed cannot be recovered.
* Spelling corrections for states are based on the mappings in the script.
* Extend the `.replace()` mappings if your dataset contains more variations.
