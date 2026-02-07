# SSIS_Multicast_Excel_To_Local_And_AWS_RDS

This project demonstrates a complete SSIS ETL pipeline that reads data from three Excel files, performs sorting and merging transformations, and loads the final processed data into both a local SQL Server database and an AWS RDS (SQL Server) database.  
By using the Multicast transformation, the same data stream is delivered in parallel to on-premises and cloud destinations, representing a real-world hybrid data integration scenario.

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

All three Excel files contain the same structure:

- id  
- First_name  
- Last_name  
- gender  
- Phon_Company  
- month  

---

## 🧭 Control Flow

<img width="1920" height="1080" alt="Screenshot (789)" src="https://github.com/user-attachments/assets/f22096da-8368-46ab-a19d-3143c0588199" />

The Control Flow contains two main tasks:

### 1. Execute SQL Task

Before loading any data, the destination table is cleaned using the following command:

```sql
TRUNCATE TABLE Task4;
