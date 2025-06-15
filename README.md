# 🧾 Invoice Extraction

This Python project extracts data from Amazon and Flipkart invoices in PDF format and organizes it into an Excel file. It processes header information (e.g., Order Number, Sold By) and table data (e.g., product details, quantities) using hardcoded logic, without relying on third-party APIs.

---

## ✨ Features

- 📄 Extracts header fields:
  - **Amazon**: Order Number, Invoice Date, Sold By
  - **Flipkart**: Order ID, Invoice Date, Bill To
- 📊 Scrapes product table data: **Description**, **Quantity**, **Total Amount**
- 📈 Outputs to `invoices.xlsx` with **one sheet per invoice**
- 🛠️ Includes **error handling** and **debug logs** for unknown formats or missing data
- 🔢 Supports a predefined set of **8 sample invoices** (4 Amazon, 4 Flipkart)

---

## 🗂️ Project Structure

```

invoice-extraction/
├── index.py                   # 🧠 Main Python script for data extraction
├── input/                     # 📥 Folder for input PDF invoices (ignored by Git)
├── output/                    # 📤 Folder for output Excel and debug files (ignored by Git)
├── .gitignore                 # 🚫 Specifies files/folders to ignore in Git
└── README.md                  # 📘 Project documentation

````

### 📁 File/Folder Descriptions

- `index.py`: Core script for processing PDFs and generating Excel output
- `input/`: Stores input PDFs (e.g., `Iphoneinvoicev2.pdf`, `OD333957328941392100-4.pdf`)
- `output/`: Contains `invoices.xlsx` and debug files (e.g., `debug_Iphoneinvoicev2.pdf.txt`)
- `.gitignore`: Excludes `input/`, `output/`, cache, and virtual envs from Git

---

## 🔧 Prerequisites

- 🐍 Python **3.8+**
- Required Libraries:

```bash
pip install pdfplumber pandas openpyxl
````

---

## 📥 Input PDFs

Place the following invoices in the `input/` folder:

### 🛒 Amazon

* `Iphoneinvoicev2.pdf`
* `1.1.pdf`
* `award_1.pdf`
* `Bag invoice main (1).pdf`

### 📦 Flipkart

* `OD333957328941392100-4.pdf`
* `OD330090353912332100.pdf`
* `OD334595557473718100.pdf`
* `OD332423168587976100.pdf`

---

## ⚙️ Installation

### 🔁 Clone the Repository

```bash
git clone https://github.com/Dnyaneshwarigund12/Invoice_extraction.git
cd invoice-extraction
```

### 📦 Install Dependencies

```bash
pip install pdfplumber pandas openpyxl
```

### 📂 Set Up Input Files

* Copy the required PDF invoices into the `input/` folder
* Ensure **file names match exactly** (case-sensitive)

---

## ▶️ Usage

### 🚀 Run the Script

```bash
python index.py
```

### 📊 Check Output

* Output Excel: `output/invoices.xlsx`

  * ✅ **Summary sheet** with processing status
  * 📃 **One sheet per invoice** with:

    * Header data (e.g., Order Number, Sold By)
    * Table data (e.g., Description, Qty)
    * Or a message if no table data found

* 🐞 Debug logs: `output/debug_*.txt` (for unidentified invoice types)

---

## 📤 Output Format

### 📁 Excel File: `output/invoices.xlsx`

#### 📝 Summary Sheet

* Lists each PDF’s status (e.g.:
  `"Processed: 1.1.pdf (Amazon)"`,
  `"No table data found in Iphoneinvoicev2.pdf"`)

#### 📄 Invoice Sheets

* **Header data** in columns A and B (e.g., `Order Number: 405-1234567-8901234`)
* A blank row separator
* **Table data** with headers (e.g., `Description`, `Qty`, `Total`)
* If no table data is available, includes a message

---

## 🧠 Notes

### 🕵️ Invoice Type Detection

* **Amazon**: Identified by `"Tax Invoice/Bill of Supply/Cash Memo"`, `"amazon.in"`, or `"HSN"`
* **Flipkart**: Identified by `"Flipkart"`, `"FSN:"`, or `"Thank You!"`

### 🔍 OCR Limitations

* Some PDFs (e.g., `Iphoneinvoicev2.pdf`) may have incomplete tables due to OCR issues
* Script uses fallback logic for better text-based extraction
* **Text-based PDFs work best** (not scanned images)

### 🔐 Sensitive Data

* `.gitignore` ensures `input/` and `output/` are not committed
* Protects personal data like addresses

---

## 🛠️ Troubleshooting

### ❓ Unknown Invoice Types

* Check `output/debug_*.txt` files for raw text
* Update detection logic in `get_invoice_type()` as needed

### 📉 Missing Table Data

* Confirm PDFs are **text-based**
* Use OCR tools like `tesseract` for scanned files
* Adjust `extract_tables` logic if necessary

### 📁 File Not Found

* Ensure **file names match** those in the script

### 📦 Dependencies

If using a `requirements.txt`:

```
pdfplumber
pandas
openpyxl
```

Install with:

```bash
pip install -r requirements.txt
```

---

## 🤝 Contributing

* Fork the repository and submit pull requests
* Report bugs or request features via **GitHub Issues**

---

## 📄 License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.

---
