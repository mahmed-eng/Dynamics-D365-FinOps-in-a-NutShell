?? Form Functional Description with Events and Logic
1. OnEnter (Event Handler on String Control)Triggered when the user presses Enter after typing in the input field (e.g., Voucher Number).
Captures the user-entered value from a FormStringControl and stores it in a variable for use in the search logic.

2. Search Button (Voucher Lookup + Field Population)
On click:
Retrieves the voucher number entered via the OnEnter event.
Searches the LedgerJournalTrans table using that voucher number.
If a match is found:
Transfers relevant data (date, amount, vendor info) into a temporary table (DIN_TransferMFGVendorTempTable).
Refreshes the form grid/data source to show the data.
If no match is found, a warning message is shown.

3. OnLookup (Dropdown for Manufacturing Vendors)
Provides a filtered lookup/dropdown list of available MFG Vendors.
Typically tied to the ToMFGVendor field.
Uses SysTableLookup or custom query logic for vendor filtering based on business rules.

4. OnModified (After Vendor Selection from Dropdown)
Triggered when a user selects a vendor from the lookup/dropdown.
Automatically populates related fields (e.g., ToMFGVendorName) based on the selected vendor number.
Ensures consistency and prevents manual data entry errors.

5. Transfer Button (LedgerJournalTrans Update)
On click:
Reads the current record from the temp table (DIN_TransferMFGVendorTempTable).
Matches the voucher number with a record in LedgerJournalTrans.

If a match is found:
Updates the VendorNumber and VendorName fields in LedgerJournalTrans using forUpdate and tts transaction.
Deletes all records from the temp table.
Re-fetches the updated LedgerJournalTrans record.
Re-inserts it back into the temp table and refreshes the form's data source to reflect the update.

If no match is found, a warning is displayed.

