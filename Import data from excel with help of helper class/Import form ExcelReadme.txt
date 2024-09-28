DinBarcodeUtility - Barcode Management for Items
Overview
The DinBarcodeUtility class is a form designed for barcode management of retail items in a Dynamics 365 for Finance and Operations (D365 F&O) environment. It includes functionalities to filter and manage barcodes based on hierarchy and item IDs, and allows importing and updating barcodes from Excel spreadsheets. The form uses multiple lookup controls to filter records and features buttons to update and import barcodes, as well as handle associated data validation.

Features:
Barcode Lookup: Users can filter barcodes based on item hierarchy, item ID, and barcode.
Item Hierarchy Lookup: Select item hierarchy levels and filter items accordingly.
Barcode Updates: Update barcodes for items using predefined lookup filters and specific date ranges.
Excel Import: Import barcodes from an Excel spreadsheet with validation checks for barcode integrity.
Multi-level Filtering: Dynamic filtering of records using query logic based on hierarchy and item ID.
Error Handling: Logs and handles errors during barcode imports to ensure data consistency.
Key Components
Classes and Controls
Form Initialization (init):

Initializes the form with default values (All) for the hierarchy, item ID, and barcode fields.
Deletes any previously cached data from the DinBarcodeUtility table.
Hierarchy Lookup:

A lookup control that retrieves the item hierarchy levels from the EcoResCategory table and uses multi-select control for selecting multiple hierarchy levels.
Item ID Lookup:

Filters item IDs based on the selected hierarchy. Also applies a date range filter to ensure items are retrieved within the specified creation date range.
Barcode Lookup:

Filters barcodes based on the selected item IDs. This control links InventItemBarcode to the selected items and allows multi-select filtering.
Update Button:

On clicking the button, the selected hierarchy, item IDs, and barcodes are used to fetch and update records in the DinBarcodeUtility table.
Data is fetched from multiple tables (InventItemBarcode, DinRetailHierarchyViewLevel, etc.) based on the selected criteria and date ranges.
Import Button:

Handles barcode imports from an Excel file.
Validates the imported barcodes and inserts valid records into the DinBarcodeUtility table.
Uses OfficeOpenXml library for reading Excel files.
Performs error handling to ensure any invalid barcodes are logged and displayed to the user.
Import with Item ID Button:

Similar to the Import button, but adds functionality to import item-specific barcodes and additional item details such as color and size.
Setup and Installation
Prerequisites
Dynamics 365 for Finance and Operations environment.
EPPlus Library for reading and processing Excel files (OfficeOpenXml).
Necessary permissions to access and modify InventItemBarcode, EcoResCategory, DinRetailHierarchyViewLevel, and DinBarcodeUtility tables.
How to Install
Copy the provided class code into your Dynamics 365 development environment.
Ensure the required tables (DinBarcodeUtility, InventItemBarcode, etc.) exist in your database.
Add the EPPlus library to your project for Excel file handling.
Compile the form and deploy it in your D365 environment.
How to Use
Open the DinBarcodeUtility form.
Use the Hierarchy, Item ID, and Barcode fields to filter the data.
Click the Update button to refresh and update the filtered data.
For Excel imports, click the Import or Import with Item ID button, select the Excel file, and import the data.
Excel Import Format
The Excel file for importing barcodes must have the following columns:

Column 1: Barcode (required)
Column 2: Quantity (optional)
Make sure the barcodes are valid before importing to avoid errors.

