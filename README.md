# CPG Samples Database – User Guide

The database stores and manages data on samples processed in the ancient and modern DNA lab at the Centre for Palaeogenetics (CPG).

You can access the database here: https://palaeogenetics.com/cpg_database

This repo is also the place to **report bugs and suggest changes** (see [Support](#9-support)).

## Contents
1. [Getting Started](#1-getting-started)
2. [Modules and Sub-Modules](#2-modules-and-sub-modules)
3. [Primary Key](#3-primary-key)
4. [Finding Records](#4-finding-records)
5. [Adding/Importing Records](#5-addingimporting-records)
6. [Editing Records](#6-editing-records)
7. [Downloading Records](#7-downloading-records)
8. [Deleting Records](#8-deleting-records)
9. [Support](#9-support)

## 1. Getting Started
Create an account using the **Sign Up** button on the login page. Fill out the required fields (select your PI's name in the group drop-down list). **Your account is not active right away** – wait for the email confirming that the admin has approved it, then sign in.

Once signed in, you can:
- View records in all modules and sub-modules
- Add records in all modules and sub-modules
- Edit records that belong to you or your group
- Delete records that belong to you

Click your username (top-right corner) to see your account details, change your email or password, and see your permissions. If you need additional permissions, contact the admin!

## 2. Modules and Sub-Modules
The database has four main modules, one per sample type: **Ancient Animal (AA)**, **Modern Animal (MA)**, **Environmental (E)** and **Human (H)**. Each has the sub-modules *Sample Information*, *DNA Extraction*, *DNA Library* and *Sequencing*.

The extra module **General (G)** holds data shared among sample types: *Index Sequences*, *Name Abbreviations* and *Extra Files*. (Please add your full name and code in *Name Abbreviations* after signing up.)

### Ancient Animal (AA) Samples
**Sample Information** – Key, Lab ID, Sample ID, collection name, collection no, material, taxon, sex, country, region, site, latitude, longitude, geological age, year of death, 14C ID, 14C date (uncal), 14C error, supplier, endogenous DNA (%), complexity (%), comments, taxon (MOR) (taxon suspected by morphology), picture (link).

*Endogenous DNA* and *complexity* are filled automatically once sequencing data for the same Lab ID is added in *Sequencing*. The last columns show how many extracts, libraries and sequencing records exist for the sample. Click a number to jump to those records, or open the sample and scroll down.

**DNA Extraction** – Lab ID, Extract ID, protocol, processed by, extraction date, sample weight (mg), volume (ul), concentration (ng/ul), storage, project, comments.

**DNA Library** – Lab ID, Library ID, protocol, processed by, library date, storage, amplification enzyme, volume (ul), Cq value, concentration (ng/ul), project, comments, TapeStation (link).

**Sequencing** – Lab ID, Library ID, Sequencing ID, platform and setup, P7-P5 ID (P7 and P5 sequences are filled from *Index Sequences*), raw/merged/mapped/filtered/unique reads, reference genome, mapping program, read length cutoff, MQ filter, PCR duplicates, complexity, endogenous DNA, GRR, coverage, mito coverage, min/max/mean/median read length, deep sequenced (YES/NO), comments, mapDamage/AMBER (link).

### Modern Animal (MA) Samples
**Sample Information** – Key, Lab ID, Sample ID, material, taxon, country, region, sex, age (years), collection date, sampling method, supplier, comments, picture (link).

**DNA Extraction** – same as AA.

**DNA Library** – same as AA, without amplification enzyme and Cq value.

**Sequencing** – Lab ID, Library ID, Sequencing ID, platform and setup, P7-P5 ID, raw/mapped/filtered reads, reference genome, mapping program, MQ filter, coverage, mito coverage, min/max/mean/median read length, comments.

### Environmental (E) Samples
**Sample Information** – Key, Lab ID, Sample ID, country, region, site, section name, section location, sediment type, sediment temp, temp method, replicates, sampling approach, geological age, latitude, longitude, collected by, collection date, depth from exposure base (m), depth from section base (cm), sample storage, comments, picture (link).

**DNA Extraction** and **DNA Library** – same as AA (no taxon).

**Sequencing** – same as AA, without read length cutoff, PCR duplicates, complexity, endogenous DNA, GRR and deep sequenced.

### Human (H) Samples
**Sample Information** – Key, Lab ID, Sample ID, collection name, collection nr., material, country, region, site, latitude, longitude, 14C date (uncal), 14C error, 14C ID, supplier, endogenous DNA (%), complexity (%), comments, picture (link). Endogenous DNA and complexity are filled automatically from *Sequencing*, as in AA.

**DNA Extraction** and **DNA Library** – same as AA (no taxon).

**Sequencing** – same as AA, without read length cutoff and merged endogenous DNA.

**Good to know (all modules):**
- **Taxon** in Extraction, Library and Sequencing comes automatically from *Sample Information*.
- The **Lab ID must already exist** in *Sample Information* before you can add extracts, libraries or sequencing for it. The same goes for the Library ID (Sequencing) and the P7-P5 ID (*Index Sequences*).
- Write dates as **YYYY.MM.DD** (e.g. 2025.10.08).

## 3. Primary Key
The **Key** in each sub-module is a unique number the database gives every record. No two records can have the same Key. It is used to update records through CSV import (see [Editing Records](#6-editing-records)), so never change it.

## 4. Finding Records
- **Quick search** – type in the search box above the table. Use the drop-down next to it to search **one column only** (e.g. Lab ID) instead of all columns.
- **Filters** – click **Filter** for more detailed searches (e.g. *Lab ID contains AVM* and *Project is exactly Hippos_UK*). Add or remove conditions as needed, then click **Apply filters**. To see only your own records, select **Only your own records**.
- **Added by** – every table has an *Added by* column showing who added each record. It is also shown at the top of each record.

## 5. Adding/Importing Records
**Single record:** open the sub-module, click **Add New**, fill in the fields (compulsory fields have a red star) and click **Save New**.

**Many records (CSV import):** start from the [CSV templates](csv_templates) and keep the column names as they are.
1. Click **Import CSV data** (top bar) and select your file.
2. **Which table should the data go into?** – select the sub-module.
3. **What should happen with the records?** – choose one:
   - *Add new records only* – for new records. Rows whose Key already exists are skipped.
   - *Update existing records and add new ones* – for editing (see below).
4. **File format** – the defaults work for files saved from the database or from the templates.
5. **Check the columns** – every column of your file is matched to a field. Red columns are skipped.
6. Click **Import CSV data**. At the end you get a summary of what was added, updated and skipped. Click **Show details** to see the row number and Key of any skipped rows and why they were skipped.

## 6. Editing Records
**Single record:** click the record, make your changes and click **Save Changes**.

**Many records:**
1. Select the records you want to edit (tip: use Filters with *Only your own records* to find all your records).
2. Click **Save N selected as CSV** – every row includes its **Key**.
3. Open the CSV in Excel (etc.), make your changes and save it as CSV. Don't change or delete the Key column!
4. Import the file and choose **Update existing records and add new ones**. And voilà!!

Remember you can only edit records that belong to you or your group.

## 7. Downloading Records
Select the records you want and click **Save N selected as CSV** – only those records are downloaded. With nothing selected, **Save CSV** downloads all records matching your current search and filters.

## 8. Deleting Records
Select the records in the table, open the **More** drop-down and click **Delete**. Remember you can only delete records that belong to you.

## 9. Support
Found a bug or have a suggestion? Please [open an issue](../../issues) in this repo. You can also contact me on Slack or by email: bilal.sharif@su.se

