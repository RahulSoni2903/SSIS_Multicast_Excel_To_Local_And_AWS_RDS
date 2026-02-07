# SSIS_Multicast_Excel_To_Local_And_AWS_RDS

This project demonstrates a complete end-to-end SSIS ETL pipeline that reads data from three Excel files, sorts and merges them using SSIS transformations, and finally loads the processed data into two different destinations in parallel:
- ✅ Local SQL Server Database
- ✅ AWS RDS (SQL Server) Cloud Database

The project showcases a real-world hybrid data integration scenario using SSIS Multicast.

---

## 📌 Project Objective

To design an SSIS package that:

- Reads data from three Excel source files
- Sorts all Excel data by ID
- Merges Excel File 1 and Excel File 2
- Merges the result with Excel File 3
- Sends the final merged dataset to:
  - Local SQL Server (sorted by Month)
  - AWS RDS SQL Server (sorted by First Name)

---

## 🛠 Tools & Technologies

- SQL Server Integration Services (SSIS)
- Microsoft Excel (Source files)
- SQL Server (Local database)
- AWS RDS – SQL Server (Cloud database)
- Visual Studio (SSDT)

---

## 📊 Source Excel Files

### Excel 1
<img width="497" height="247" alt="Excel1" src="https://github.com/user-attachments/assets/a0f24a4b-c11e-4f60-a2c4-7bf03083e965" />

---

### Excel 2
<img width="494" height="256" alt="Excel2" src="https://github.com/user-attachments/assets/d23bb25a-b11b-4021-af84-15b6b8841aaf" />

---

### Excel 3
<img width="542" height="249" alt="Excel3" src="https://github.com/user-attachments/assets/4e26345e-8b91-4e23-86f1-de9995fdd45c" />

---

## 🧩 Overall Package Architecture

The SSIS package is divided into two main parts:

- Control Flow
- Data Flow

---

## 🔁 Control Flow Design

<img width="1920" height="1080" alt="Screenshot (789)" src="https://github.com/user-attachments/assets/f22096da-8368-46ab-a19d-3143c0588199" />

### Control Flow contains two tasks:

### 1️⃣ Execute SQL Task  
This task runs the following command before loading new data:


Purpose:
- Removes old data from the destination table before loading fresh records.
- Command :- TRUNCATE TABLE Task4
---

### 2️⃣ Data Flow Task  
This task performs all data extraction, transformation and loading operations from Excel to databases.

---

## 🔄 Data Flow Design

<img width="1920" height="1080" alt="Screenshot (790)" src="https://github.com/user-attachments/assets/295d1ed1-ebe6-4cfb-b0d4-7cf6747afd17" />

The Data Flow performs the following steps:

---

### Step 1 – Read data from three Excel files

- Excel Source 1
- Excel Source 2
- Excel Source 3

---

### Step 2 – Sort transformation on all Excel sources

All three Excel inputs are sorted by ID:
### Step 3 – Merge Excel File 1 and Excel File 2

- The first Merge transformation combines Excel 1 and Excel 2 based on the sorted ID.

---

### Step 4 – Merge the result with Excel File 3

- A second Merge transformation is used.
- The output of the first merge is merged with Excel 3.

---

### Step 5 – Multicast Transformation

After all three Excel files are merged, the final dataset is passed into a Local Server and Cloud Server:
## 📤 Parallel Data Load Using Multicast

From the Multicast output, data is sent to two different paths.

---

### 🟢 Path 1 – Local SQL Server Database

- A Sort transformation is applied
- Data is sorted by Month:
### 🔵 Path 2 – AWS RDS SQL Server Database

- A separate Sort transformation is applied
- Data is sorted by First Name:
## ✅ Local Database Verification

<img width="1920" height="1080" alt="Local Databse" src="https://github.com/user-attachments/assets/ffb16ec1-8549-4803-a42e-f9984c4d935c" />

The above screenshot confirms that the data is successfully loaded into the Local SQL Server database.

---

## ☁ AWS Cloud Database Verification

<img width="1920" height="1080" alt="Cloud Data" src="https://github.com/user-attachments/assets/5410016e-6657-4f85-91eb-aad3071982e7" />

The above screenshot confirms that the data is successfully loaded into the AWS RDS SQL Server database.

---

## ☁ AWS RDS Cloud Database View

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b548b330-574e-405a-a268-5c44f33b2c92" />

This image shows the cloud database table containing the final processed data.
