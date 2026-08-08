Transaction Records Deduplication Project

A data cleaning and quality-assurance project built in Excel that identifies, classifies, and resolves duplicate transaction records collected from two source systems (CRM and ERP).

📋 Overview

Organizations that pull transaction data from multiple systems often end up with duplicate, near-duplicate, or inconsistent records. This project takes a raw transaction dataset containing several types of duplication issues and applies a systematic cleaning process to flag, classify, and produce a trustworthy, deduplicated dataset.

🗂️ Workbook Structure

The workbook contains two sheets:

1. Sheet1 — Raw Data

The original, unprocessed transaction records as pulled from the source systems, containing:

Column	Description
Transaction ID	Unique identifier assigned to each transaction
Customer Name	Name of the customer
Product	Product purchased
Amount	Transaction value
Date	Transaction date
Status	Transaction status (Completed, Pending, Refunded, etc.)
Source System	Origin system of the record (CRM or ERP)

This sheet intentionally includes messy, real-world issues: exact duplicates, cross-system duplicates, inconsistent name spellings, mismatched statuses, and mismatched dates for the same transaction ID.

2. Cleaned Data — Processed & Classified Data

The same records enriched with analytical columns that detect and categorize duplication:

Column	Purpose
Duplicate Type	Classifies the nature of the duplicate (see categories below)
Composite Key	Concatenated key used to detect matching records
Is Duplicated	Boolean flag (TRUE/FALSE) marking duplicated rows
TID Count	Number of times a Transaction ID appears in the dataset
Duplication Risk	Risk level assigned to the record (Clean, High Risk)
Deduplicated Dataset	The final, cleaned set of unique transaction records

This sheet also includes a side-by-side breakdown at the bottom, separating Duplicate Rows from Clean Rows for quick auditing.

🔍 Duplicate Categories Identified

The project distinguishes between several real-world duplication patterns:

Exact Duplicate — Identical records repeated in full
Cross-System Duplicate — Same transaction logged separately in both CRM and ERP
Fuzzy Duplicate — Same transaction with minor inconsistencies (e.g., name spelling variations like "Khalid Al-Otaibi" vs. "Khalid Alotaibi")
Temporal Duplicate — Same transaction recorded with a different date
Partial Duplicate — Same transaction with a conflicting field (e.g., a missing/blank status)
Not a Duplicate — Unique, clean transaction records
⚙️ Methodology
Composite Key Generation: Combine key fields (Transaction ID, Customer, Product, Amount, Date) into a single string to detect matches
Duplicate Detection: Count occurrences of each Transaction ID / composite key across the dataset
Classification: Apply logic to categorize each duplication case into one of the types above
Risk Scoring: Flag records as Clean or High Risk based on duplication severity
Deduplication: Produce a final clean dataset retaining only unique, validated transactions
🛠️ Tools Used
Microsoft Excel (formulas: COUNTIF/COUNTIFS, CONCATENATE, conditional logic, boolean flags)
🚀 How to Use
Open transaction-records-project.xlsx
Review Sheet1 for the original raw dataset
Review the Cleaned Data sheet to see:
How each row was classified
Which rows were flagged as duplicates vs. clean
The final deduplicated dataset ready for reporting or downstream use
📊 Use Case

This kind of workflow is commonly used in data quality assurance, data migration, and system integration projects — for example, when merging records from a CRM and an ERP system and needing a single source of truth for reporting or analytics.

This project was created as a data cleaning and deduplication exercise, demonstrating practical techniques for identifying and resolving data quality issues in multi-source datasets.
