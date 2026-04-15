# 📄 CSV / TSV Message Extractor

A simple drag-and-drop web tool to extract and clean messaging data from CSV/TSV files.

---

## 🚀 Overview

This project allows you to:

* Drag & drop a CSV/TSV file
* Automatically detect columns
* Extract:

  * `RECEIVER → NUMBER`
  * `STATUS`
  * `ERROR → REASON`
* Output clean tab-separated data
* Copy results instantly

---

## 🧩 Input Format

Your file should contain columns like:

```id="v7s1pd"
ID	MESSAGE INDEX	MESSAGE TYPE	UID	NAME	RECEIVER	STATUS	SENT	DELIVERED	READ	REPLIED	REPLY TYPE	REPLY	FAILED	ERROR
```

---

## 📤 Output Format

```id="z9c3ml"
NUMBER	STATUS	REASON
919666347944	delivered	
918639782066	failed	This message was not delivered...
917780588638	read	
```

---

## ✨ Features

* Drag & Drop upload
* Supports CSV and TSV
* Smart column detection (case-insensitive)
* No backend required
* Copy output instantly

---

## 🛠️ How It Works

1. Drag and drop your file into the upload area
2. The app reads the file in the browser
3. Detects delimiter (comma or tab)
4. Finds required columns:

   * `RECEIVER`
   * `STATUS`
   * `ERROR`
5. Renames:

   * `RECEIVER → NUMBER`
   * `ERROR → REASON`
6. Displays formatted output
7. Click **Copy Output**

---

## 📦 Setup

### Option 1: Run Locally

* Save the HTML file
* Open it in your browser

### Option 2: Deploy with Docker

```yaml id="q8m4xr"
version: "3.8"

services:
  csv-tool:
    image: busybox:latest
    container_name: csv-tool
    command: httpd -f -p 80 -h /www
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/www/index.html:ro
```

Run:

```id="p3n8yb"
docker-compose up -d
```

Then open:

```id="d5k2ws"
http://localhost:8080
```

---

## 📁 Project Structure

```id="x2l9op"
project/
│── docker-compose.yml
│── index.html
```

---

## ⚠️ Limitations

* Does not handle complex quoted CSV data
* Large files may slow down browser
* Requires columns:

  * RECEIVER
  * STATUS
  * ERROR

---

## 🔮 Future Improvements

* Excel (.xlsx) support
* Filtering options (FAILED / DELIVERED)
* Download output as file
* Data preview table

---

## 📌 Summary

A fast, minimal tool to clean and extract messaging data directly in the browser with zero backend setup.
