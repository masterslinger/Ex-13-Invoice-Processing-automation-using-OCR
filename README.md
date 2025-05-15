# Ex-13-Invoice-Processing-automation-using-OCR

~~~
Name : M.JOHNPALL
Reg.No : 212224040140
~~~

## Aim
To automate the extraction of key information (Invoice Number, Date, and Total Amount) from a scanned invoice PDF using OCR technology in UiPath and store the extracted data into an Excel file.

## Materials Required
UiPath Studio

Tesseract OCR or Microsoft OCR (included in UiPath)

Invoice PDF file (scanned or image-based)

UiPath.Excel.Activities

UiPath.PDF.Activities

Basic understanding of Regular Expressions (Regex)

Microsoft Excel

## Procedure
Step 1: Prepare the Project
Create a new project in UiPath Studio called InvoiceOCRBot.

Place your Invoice PDF in the project folder for easy access.

Step 2: Read the Invoice using OCR
Use the Read PDF with OCR activity (from UiPath.PDF.Activities).

Set the file path to your invoice PDF.

Use Tesseract OCR or Microsoft OCR engine.

Output: ocrText (String variable)

Step 3: Extract Data Using Regex
Use Assign activities to extract data:

~~~
invoiceNumber = System.Text.RegularExpressions.Regex.Match(ocrText, "Invoice Number[:\s]*([A-Za-z0-9\-]+)").Groups(1).Value  
invoiceDate = System.Text.RegularExpressions.Regex.Match(ocrText, "Date[:\s]*([0-9\/\-]+)").Groups(1).Value  
totalAmount = System.Text.RegularExpressions.Regex.Match(ocrText, "Total Amount[:\s]*([\d,]+\.\d{2})").Groups(1).Value
~~~

 Step 4: Create and Write to Excel
Use a Build Data Table activity to create a table with columns:
Invoice Number, Date, Total Amount

Use Add Data Row to insert extracted values.

Use Write Range activity to save the data to InvoiceData.xlsx.

Step 5: Run and Verify
Run the bot.

Open the InvoiceData.xlsx file to check if the data is entered correctly.

## OUTPUT:
![image](https://github.com/user-attachments/assets/4ec0ce4d-4329-449a-ac1e-185eb1391e7a)

![image](https://github.com/user-attachments/assets/ffc51de5-3e48-4f29-8c38-39b755f52759)

![image](https://github.com/user-attachments/assets/a3abd43c-fbaf-46ab-9551-634d0ec2fea6)

## Result
The UiPath robot successfully extracted key data from an image-based PDF using OCR and saved it in an Excel file for further use.
