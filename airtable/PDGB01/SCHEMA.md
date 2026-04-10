# PDGB01 - Airtable Base Documentation

**Base ID:** `appuqtEsYmO4q8IE4`  
**Last Updated:** 2026-04-09 21:53:00  
**Total Tables:** 20  

## Table of Contents

- [T01_Job_List](#t01_job_list)
- [T02_Proposals](#t02_proposals)
- [T03_Invoices](#t03_invoices)
- [T04_Vendors](#t04_vendors)
- [T05_Clients](#t05_clients)
- [T06_Project Vendors](#t06_project-vendors)
- [T07_Vendor Expense](#t07_vendor-expense)
- [T08_Proposal Vendor Estimates](#t08_proposal-vendor-estimates)
- [T09_Jurisdictions](#t09_jurisdictions)
- [T10_Permit Types](#t10_permit-types)
- [T11_Permit Applications](#t11_permit-applications)
- [T12_File Managers](#t12_file-managers)
- [T13_Staff](#t13_staff)
- [T14_Building Archive](#t14_building-archive)
- [T15_Contacts_Outdated](#t15_contacts_outdated)
- [T16_Matterport](#t16_matterport)
- [T17_KPIs](#t17_kpis)
- [Grid view](#grid-view)
- [T15_Contacts](#t15_contacts)
- [Grid view 3](#grid-view-3)
- [Relationships](#relationships)

---

## T01_Job_List

**Table ID:** `tbl6eilFaVl5XOT8x`  
**Primary Field:** fldziPbYt7Hiozyup  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| JOB NAME & NO | `formula` | - | Formula: `CONCATENATE({fldOBIxfCMHUbgeiB}, " ", {fldt0S1JAyy...` |
| JOB NUMBER | `singleLineText` | - | - |
| Project Lead | `multipleRecordLinks` | Linked to T13_Staff | Links to: `tblZl5HNB9mhDIlHc` |
| Email (from Project Lead) 2 | `multipleLookupValues` | - | - |
| Requires Matterport | `checkbox` | - | - |
| Requires Point Cloud | `checkbox` | - | - |
| Project Year | `formula` | - | Formula: `LEFT({fldOBIxfCMHUbgeiB}, 2)` |
| STATUS | `singleSelect` | Project Statuses are as follows:  - Inquiry until an FA is issued  - Prospect until FA is accepted  - Active until completed  - Finished after final invoice is issued  - Cold if the job is lost before becoming active  - Inactive if paused by the client after FA is accepted | Choices: INQUIRY, PROSPECT, ACTIVE, PAUSE, FINISHED, COLD, INACTIVE |
| JOB NAME | `multilineText` | - | - |
| SUB TYPE | `multipleSelects` | IFBP | Choices: 3D IMAGES, 3D MODEL, acreage sub-division, Addition & Reno, Addition, ADU - Add Dwell Unit, B/F washroom reno, Barn, House - Barndominium, Barrier Free, House - Bsmt Devm't, Bow Trail Alignment Shift Bar'r, Code & LUB Compliance, House - Cabin, Cannibis Cultivator, Int Reno, Contract Admin, Contract Drafting, IFDP - Change of Use, DAB Consult, Daycare DP Consult, Demising wall, Design Consult, detached garage, Master Planning, Medical Office Reno, Dog Kennel, House - Earth, Equestrian Facility, Egress Plan, Exiting review, Ext Finish Consult, Ext Facelift, Ext Reno, Exterior Panels - Shop dwgs, Fitness Studio TI, Garage - Detached, Garage - w Secondary Suite, Gymnastics Club, House - New, House - Addition, House - Move, Landscape Design, Landuse Re-designation & DP application, site plans , Major Renovation, Marketing Imagery, Meat Processor, Micro Cultivation Facility, mobile home site plan, House - New Acreage Home, Church - reno, Funeral Home - New, Restaurant - Reno, Retail - New, House - New TF, Warehouse - New, Warehouse - Reno, Office - New, Office - Reno, Office - Addition, Office - Space Plan, Parking - Structure, Parking - Feasibility Study, House - Patio Addition, Play Ground, PM support, House - Pool, Portfolio Submission, POST FIRE RECONSTRUCTION DRAWINGS, Pre-construction Services, Warehouse - Racking, rainfall dwg, Record Dwgs, Renderings, reno seacan, Schematic Design, House - Second Flr Addition, SECOND FLOOR OFFICE RENO DP & BP, House - Secondary Suite , site grade consult, Site Plan, spec greenhouse dwgs, Steel Shop Dwgs, store demising wall, store Reno, House - Straw, Structural Drawings, team building, Template, House - Tiny Home, various site devm't options, Fitness - Volleyball, Warehouse - Egress, Warehouse - Mezzanine Reno, Warehouse - Office, Warehouse - office show suite, Washroom ABC compliance, Window Shops, IFC Drawing, As-Built Drawings, Acreage Home - New Build, Acreage Home - Renovation, Exit study, Multi-Family, Fitness - Cheer, Int Finish Consult, House - Vacation, Funeral Home - reno & addt'n, Matterport Scan, Millwork Shops, new interior build-out, MatterPort, IFBP |
| PROJECT NOTES | `richText` | - | - |
| TYPE | `singleSelect` | - | Choices: RESID, COMM , CHURCH, Other, Landscape, LGS Prefab, RENDER, Steel Detailing, Matterport, Compliance |
| LOCATION - dep | `multilineText` | - | - |
| ROUGH FEE EST | `currency` | Gut sense of fee on first inquiry or budget given by client | Precision: 2 |
| % ODDS | `percent` | - | Precision: 0 |
| 1ST CONT | `date` | - | - |
| PROP DATE | `multipleLookupValues` | - | - |
| S.F. | `number` | - | Precision: 0 |
| LEFT ON TABLE | `currency` | - | Precision: 2 |
| CLIENT TYPE | `singleSelect` | - | Choices: industry, Builder, owner, past, Owner, Industry, Designer, other, Other |
| PAST CLIENT | `singleSelect` | - | Choices: Yes, yes, no, Alignable, NO, No |
| REFERRAL TYPE | `singleSelect` | - | Choices: Industry, past client, other, LinkedIn, google, builder, HOUZZ, website, None, industry, none, NONE, Builder, no, Online, Past Client, Website, Other, owner, Prospect, Yes, yes, ?? |
| PAST CLIENT REFERRAL | `checkbox` | - | - |
| NOTES | `multilineText` | - | - |
| Clients | `multipleRecordLinks` | - | Links to: `tblIDEKXrdoetpFtG` |
| Name (from Clients) | `multipleLookupValues` | - | - |
| Vendors | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |
| Name (from Vendors) | `multipleLookupValues` | - | - |
| Primary Contact (from Vendors) | `multipleLookupValues` | - | - |
| FINISH | `date` | - | - |
| Invoices | `multipleRecordLinks` | - | Links to: `tblMjIpM1WYepdNCy` |
| Fee Billed to Date | `rollup` | Linked to T03_Invoices | Rollup field: fldDZTW4nI4pzlYij |
| Fee Remaining | `formula` | - | Formula: `{fldoC8HTSGNlHvcjU}-{fldZwlLoiFt56g8Md}` |
| % Fee Remaining | `formula` | - | Formula: `{fldZaRPsLOyNnfOt9}/{fldoC8HTSGNlHvcjU}` |
| FA x SF | `formula` | - | Formula: `SWITCH({fldBIK0UzpWXBNM6p}, "Commerical", {fldWCxX...` |
| P.O. | `singleLineText` | - | - |
| START | `date` | - | - |
| BLENDED BUDGET RATE | `currency` | - | Precision: 2 |
| ESTIMATED HOURS | `formula` | - | Formula: `{fldthflpSKDPMV09A}/{fldPxDxCBkwW7lTYF}` |
| FP ISSUED | `checkbox` | - | - |
| FINISHED | `checkbox` | - | - |
| DELIVERABLES | `multipleSelects` | - | Choices: Architectural Review & Seal, IFBP, IFP, MP virtual tour, IFDP, IFC, Space Plan, Window Shop Swgs, ifdp site plan, feasability, Millwork shop dwgs, IFDP IFBP, IFDP IFBP  |
| PHASES | `multipleSelects` | - | Choices: 0.0 - START UP, 1.0 - PROGRAM & DUE DILIGENCE, 2.0 - SCHEMATIC DESIGN, 3.0 - DESIGN DEVELOPMENT, 4.0 - INTERIOR DESIGN, 5.0 - CONSTRUCTION DOCUMENTS, 6.0 - PM - PRE CONSTRUCTION, 7.0 - PM - ACTIVE CONSTRUCTION |
| TEAM STATUS | `singleSelect` | - | Choices: Active, Archived, Not Created |
| ARCHIVE DATE | `date` | - | - |
| FILE SIZE | `number` | File Size (MB) | Precision: 2 |
| Project Vendors | `multipleRecordLinks` | - | Links to: `tbl4yOMTINASBer7u` |
| PRJT VNDRS | `multipleRecordLinks` | - | Links to: `tbl4yOMTINASBer7u` |
| VENDOR FEE | `rollup` | Linked to T04_Vendors | Rollup field: fldD6C6cg4ZTyS45J |
| VENDOR AHF | `rollup` | - | Rollup field: fldsVykaF0k7CNOj0 |
| File Managers | `multipleRecordLinks` | - | Links to: `tbl67ULST92raRDen` |
| T02_Proposals | `multipleRecordLinks` | Linked to T02_Proposals | Links to: `tblsE6Uj4DyOXCkpl` |
| Permit Applications | `multipleRecordLinks` | - | Links to: `tblICS7xCK0fyc3QC` |
| Jurisdiction | `multipleRecordLinks` | - | Links to: `tblPjNKI1SCRFUwYN` |
| FEE EST. | `rollup` | Calculated from T02 | Rollup field: fldUAWvk8iEfUkwCJ |
| TOTAL FEE. | `rollup` | Linked to T02_Proposals | Rollup field: fld7vNu98NRGtqheU |
| VENDOR EST. | `rollup` | Linked from T02_Proposals | Rollup field: fldagXPy5RnTblbig |
| AHF | `rollup` | Calculated from T02 | Rollup field: fldHVsD36URPutQ07 |
| Email (from Project Lead) | `multipleLookupValues` | - | - |
| PRIOR PROJECT | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| From field: PRIOR PROJECT | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| T14_Building Archive | `multipleRecordLinks` | - | Links to: `tblFCpYX3EApt1Yhg` |
| Specialty Standards | `multipleSelects` | - | Choices: AWSA - Agrichemicals |
| T16_Matterport | `multipleRecordLinks` | - | Links to: `tblWCIhvThgROHJQ7` |
| New Building | `singleLineText` | - | - |
| Project Scope - Cleanup | `multipleSelects` | IFBP | Choices: 3D IMAGES, 3D MODEL, acreage sub-division, Addition & Reno, Addition, ADU - Add Dwell Unit, B/F washroom reno, Barn, House - Barndominium, Barrier Free, House - Bsmt Devm't, Bow Trail Alignment Shift Bar'r, Code & LUB Compliance, House - Cabin, Cannibis Cultivator, Int Reno, Contract Admin, Contract Drafting, IFDP - Change of Use, DAB Consult, Daycare DP Consult, Demising wall, Design Consult, detached garage, Master Planning, Medical Office Reno, Dog Kennel, House - Earth, Equestrian Facility, Egress Plan, Exiting review, Ext Finish Consult, Ext Facelift, Ext Reno, Exterior Panels - Shop dwgs, Fitness Studio TI, Garage - Detached, Garage - w Secondary Suite, Gymnastics Club, House - New, House - Addition, House - Move, Landscape Design, Landuse Re-designation & DP application, site plans , Major Renovation, Marketing Imagery, Meat Processor, Micro Cultivation Facility, mobile home site plan, House - New Acreage Home, Church - reno, Funeral Home - New, Restaurant - Reno, Retail - New, House - New TF, Warehouse - New, Warehouse - Reno, Office - New, Office - Reno, Office - Addition, Office - Space Plan, Parking - Structure, Parking - Feasibility Study, House - Patio Addition, Play Ground, PM support, House - Pool, Portfolio Submission, POST FIRE RECONSTRUCTION DRAWINGS, Pre-construction Services, Warehouse - Racking, rainfall dwg, Record Dwgs, Renderings, reno seacan, Schematic Design, House - Second Flr Addition, SECOND FLOOR OFFICE RENO DP & BP, House - Secondary Suite , site grade consult, Site Plan, spec greenhouse dwgs, Steel Shop Dwgs, store demising wall, store Reno, House - Straw, Structural Drawings, team building, Template, House - Tiny Home, various site devm't options, Fitness - Volleyball, Warehouse - Egress, Warehouse - Mezzanine Reno, Warehouse - Office, Warehouse - office show suite, Washroom ABC compliance, Window Shops, IFC Drawing, As-Built Drawings, Acreage Home - New Build, Acreage Home - Renovation, Exit study, Multi-Family, Fitness - Cheer, Int Finish Consult, House - Vacation, Funeral Home - reno & addt'n, Matterport Scan, Commercial Renovation, New Home, Residential Addition, Residential Renovation, ADU, Cabin / Vacation Home, Design Consulting, Tenant Improvement, Warehouse - Renovation, Specialty / Other, 3D Renderings, Office - Renovation, Commercial Addition, Church, Mobile Home, Pre-Construction Services, Detached Structure, Exit Study, PM Support, Space Planning |
| Project SOW Items - Cleanup | `multipleSelects` | IFBP | Choices: 3D IMAGES, 3D MODEL, acreage sub-division, Addition & Reno, Addition, ADU - Add Dwell Unit, B/F washroom reno, Barn, House - Barndominium, Barrier Free, House - Bsmt Devm't, Bow Trail Alignment Shift Bar'r, Code & LUB Compliance, House - Cabin, Cannibis Cultivator, Int Reno, Contract Admin, Contract Drafting, IFDP - Change of Use, DAB Consult, Daycare DP Consult, Demising wall, Design Consult, detached garage, Master Planning, Medical Office Reno, Dog Kennel, House - Earth, Equestrian Facility, Egress Plan, Exiting review, Ext Finish Consult, Ext Facelift, Ext Reno, Exterior Panels - Shop dwgs, Fitness Studio TI, Garage - Detached, Garage - w Secondary Suite, Gymnastics Club, House - New, House - Addition, House - Move, Landscape Design, Landuse Re-designation & DP application, site plans , Major Renovation, Marketing Imagery, Meat Processor, Micro Cultivation Facility, mobile home site plan, House - New Acreage Home, Church - reno, Funeral Home - New, Restaurant - Reno, Retail - New, House - New TF, Warehouse - New, Warehouse - Reno, Office - New, Office - Reno, Office - Addition, Office - Space Plan, Parking - Structure, Parking - Feasibility Study, House - Patio Addition, Play Ground, PM support, House - Pool, Portfolio Submission, POST FIRE RECONSTRUCTION DRAWINGS, Pre-construction Services, Warehouse - Racking, rainfall dwg, Record Dwgs, Renderings, reno seacan, Schematic Design, House - Second Flr Addition, SECOND FLOOR OFFICE RENO DP & BP, House - Secondary Suite , site grade consult, Site Plan, spec greenhouse dwgs, Steel Shop Dwgs, store demising wall, store Reno, House - Straw, Structural Drawings, team building, Template, House - Tiny Home, various site devm't options, Fitness - Volleyball, Warehouse - Egress, Warehouse - Mezzanine Reno, Warehouse - Office, Warehouse - office show suite, Washroom ABC compliance, Window Shops, IFC Drawing, As-Built Drawings, Acreage Home - New Build, Acreage Home - Renovation, Exit study, Multi-Family, Fitness - Cheer, Int Finish Consult, House - Vacation, Funeral Home - reno & addt'n, Matterport Scan, Design Consulting, 3D Renderings, Building Permit, Steel Shop Drawings, Contract Administration, IFC Drawings, Pre-Construction Services, Exit Study, PM Support, Space Planning |
| Project Scope | `multipleSelects` | - | Choices: Contract Drafting, Commercial Renovation, New Home, Residential Addition, Residential Renovation, ADU, Cabin / Vacation Home, Matterport Scan, Design Consulting, Tenant Improvement, Warehouse - Renovation, Specialty / Other, Multi-Family, 3D Renderings, Office - Renovation, Steel Shop Dwgs, Commercial Addition, Code & LUB Compliance, Contract Admin, As-Built Drawings, Warehouse - New, Schematic Design, Church, Site Plan, Mobile Home, IFC Drawing, Pre-Construction Services, Office - New, Detached Structure, Portfolio Submission, Template, Exit Study, PM Support, Space Planning |
| Project SOW Items | `multipleSelects` | - | Choices: Contract Drafting, Matterport Scan, Design Consulting, 3D Renderings, Building Permit, Steel Shop Drawings, Code & LUB Compliance, Contract Administration, As-Built Drawings, Schematic Design, Site Plan, IFC Drawings, Pre-Construction Services, Portfolio Submission, Exit Study, PM Support, Space Planning |
| PDG Proposal Value | `rollup` | - | Rollup field: fldRYnlNEECNH3KbK |
| Total Proposal Value | `rollup` | - | Rollup field: fldFnyzZFTwmO6FDo |
| Referral | `singleLineText` | - | - |
| Tour URL (from T16_Matterport) | `multipleLookupValues` | - | - |
| ACC Created | `singleSelect` | - | Choices: Yes, No |
| ACC Id | `singleLineText` | - | - |
| Days Since Finish | `formula` | - | Formula: `DATETIME_DIFF(TODAY(), {fldd1BQsBN1DK71kW}, 'days'...` |
| Location - Address | `singleLineText` | - | - |
| Location - City | `singleLineText` | - | - |
| Location - Province | `singleLineText` | - | - |
| Location - Postal Code | `singleLineText` | - | - |
| Location - Unit Address | `singleLineText` | - | - |
| PROJECT BUILDER | `multipleRecordLinks` | - | Links to: `tbly6q8AulC8MpOjB` |
| Company (from PROJECT BUILDER) | `multipleLookupValues` | - | - |
| PROJECT BROKER | `multipleRecordLinks` | - | Links to: `tbly6q8AulC8MpOjB` |
| Company (from PROJECT BROKER) | `multipleLookupValues` | - | - |
| REFERRAL FROM | `multipleRecordLinks` | - | Links to: `tbly6q8AulC8MpOjB` |
| NEW CLIENT - NAME | `singleLineText` | - | - |
| LOCATION | `formula` | - | Formula: `CONCATENATE({fld9wc5IlU40OmdR4}," ",{fldEHMPim7DnJ...` |
| Created | `createdTime` | - | - |
| PDG FEE AVAIL. | `rollup` | Calculated from T02 | Rollup field: fldRYnlNEECNH3KbK |
| ANTI. MARGIN % | `rollup` | Calculated from T02 | Rollup field: fldzJwpaum8j1buMS |

### Views

- **Sync to B07** (`grid`)
- **CLEAN UP ** (`grid`)
- **Jobs without Clients** (`grid`)
- **Default View** (`grid`)
- **KEN** (`grid`)
- **Fees by Project Type** (`grid`)
- **Jobs by Client** (`grid`)
- **Jobs by Vendor** (`grid`)
- **Leslie** (`grid`)
- **Active Jobs** (`grid`)
- **Prospects** (`grid`)
- **Project Status** (`grid`)
- **Project Fees** (`grid`)
- **Team status View** (`grid`)
- **Jobs by Project Manager** (`kanban`)
- **Jobs by Jurisdiction** (`grid`)
- **Project Proposals** (`grid`)
- **Project By Year** (`grid`)
- **Projects with Building Information** (`grid`)
- **Project Contacts** (`grid`)
- **Project Matterport Information** (`grid`)
- **Projects by Prior Project** (`grid`)

---

## T02_Proposals

**Table ID:** `tblsE6Uj4DyOXCkpl`  
**Primary Field:** fldzBxidKDKDbSJt9  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Reference Number | `formula` | - | Formula: `{fldlanidOoxOtS3na}` |
| Job | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Phase/Scope | `singleLineText` | - | - |
| Proposal Status | `singleSelect` | - | Choices: Draft, Issued, Accepted, Rejected, Revision Requested, Cold, Completed |
| PDG Fee | `currency` | - | Precision: 2 |
| Available PDF Drafting Fee | `formula` | - | Formula: `{fldUAWvk8iEfUkwCJ} - {fld5ys1VBJvhSphMj}` |
| Expected Start Date | `date` | - | - |
| Expected Completion Date | `date` | - | - |
| Inquiry Date | `date` | - | - |
| Proposal Issued | `checkbox` | - | - |
| Date Issued | `date` | - | - |
| Accepted | `checkbox` | - | - |
| Rejected | `checkbox` | - | - |
| Response Date | `date` | - | - |
| Job Name | `multipleLookupValues` | - | - |
| Inquiry Age | `formula` | - | Formula: `IF({fldvVhjyY73CbkvOM},DATETIME_DIFF({fldec5rRmWvQ...` |
| Proposal Age | `formula` | - | Formula: `IF({fldIqzKMF0BhM6dS7},DATETIME_DIFF({fldU9nDJsEW9...` |
| Proposal ID (Formatted) | `formula` | - | Formula: `"PROP-" & {fldzBxidKDKDbSJt9}` |
| Proposal Vendor Estimates | `multipleRecordLinks` | - | Links to: `tblId9pw2FVXForCH` |
| Proposal PDF | `multipleAttachments` | - | - |
| Disbursable Vendor Fees | `currency` | - | Precision: 2 |
| Buried Vendor Fees | `currency` | - | Precision: 2 |
| Inquiry Response Time | `number` | - | Precision: 1 |
| T01_Job_List | `singleLineText` | - | - |
| Email (from Project Lead) (from T01_Job_List) | `multipleLookupValues` | - | - |
| Total Vendor Fees | `formula` | - | Formula: `SUM({fldyI0t8JOcv1hjac} + {fld5ys1VBJvhSphMj})` |
| Prepared By | `multipleRecordLinks` | - | Links to: `tblZl5HNB9mhDIlHc` |
| Proposal ID Number | `autoNumber` | - | - |
| FEE EST (from Job) | `multipleLookupValues` | - | - |
| AHF | `percent` | - | Precision: 2 |
| AHF Value | `formula` | - | Formula: `({fldUAWvk8iEfUkwCJ} + {fldyI0t8JOcv1hjac}) * {fld...` |
| GST | `percent` | - | Precision: 2 |
| GST Value | `formula` | - | Formula: `({fldUAWvk8iEfUkwCJ} + {fldyI0t8JOcv1hjac} + {fldH...` |
| Total Fee | `formula` | - | Formula: `{fldUAWvk8iEfUkwCJ} + {fldyI0t8JOcv1hjac} + {fldHV...` |
| AHF Value copy | `formula` | - | Formula: `({fldUAWvk8iEfUkwCJ} + {fldyI0t8JOcv1hjac}) * (1+{...` |
| PDG + Vendor Fees | `formula` | - | Formula: `{fldUAWvk8iEfUkwCJ} + {fldyI0t8JOcv1hjac}` |
| JOB NAME & NO (from Job) | `multipleLookupValues` | - | - |
| Proposal Number | `formula` | - | Formula: `IF({fldqzZkeYPMzRs4dP}, "P" & YEAR({fldux4RWp1ECWO...` |
| ANT. MARGIN % | `percent` | - | Precision: 0 |
| ANT. MARGIN $ | `formula` | - | Formula: `{fldRYnlNEECNH3KbK} * {fldzJwpaum8j1buMS}` |

### Views

- **Grid view** (`grid`)
- **Fee Calculator** (`grid`)
- **Proposal Status** (`kanban`)
- **Calendar** (`calendar`)
- ** Proposals by Estimator** (`grid`)

---

## T03_Invoices

**Table ID:** `tblMjIpM1WYepdNCy`  
**Primary Field:** fldQ4fiq0KT9qC7Xp  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Invoice Number | `singleLineText` | - | - |
| Job | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Project Name & Number | `multipleLookupValues` | - | - |
| PROJECT NAME (from Job) | `multipleLookupValues` | - | - |
| Project Name & Number Filter | `formula` | - | Formula: `{fldrlsIrjN6IQkNkI}` |
| Invoice Amount | `currency` | - | Precision: 2 |
| Includes AHF | `checkbox` | - | - |
| Billable Fee Invoiced | `formula` | - | Formula: `IF({fld5fR3IyOORjyZUW},({fldsOSFEMGMHmRmi4}-{fldF6...` |
| AHF Invoiced | `formula` | - | Formula: `IF({fld5fR3IyOORjyZUW},{fldsOSFEMGMHmRmi4}*((100/(...` |
| Vendor Expense | `multipleRecordLinks` | - | Links to: `tblflBK4iAsmcPSn8` |
| Count of Vendor Expenses | `number` | - | Precision: 0 |
| Count of Vendor Expenses Logged | `count` | - | - |
| All Vendor Expenses Logged | `formula` | - | Formula: `IF(
    OR(
        {fldtUH8LdrwnHRiz9}=0,
    ...` |
| Vendor Expense Rollup (from Invoice) (from Vendor Expense) | `rollup` | - | Rollup field: fldTotU55rYejyGr1 |
| Paid | `checkbox` | - | - |
| Date Issued | `date` | - | - |
| Date Paid | `date` | - | - |
| Calculation | `formula` | - | Formula: `DATETIME_DIFF(TODAY(), {fldZyjdxbvGYmuqX7}, 'days'...` |
| T01_Job_List | `singleLineText` | - | - |
| T01_Job_List 2 | `singleLineText` | - | - |

### Views

- **Grid view** (`grid`)
- **Vendor Expense Processing Queue** (`grid`)

---

## T04_Vendors

**Table ID:** `tblKxbn935QbK2OrM`  
**Primary Field:** fldhAWxeLTM7PmPNz  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Grid view | `multipleRecordLinks` | - | Links to: `tbly6q8AulC8MpOjB` |
| E-mail Address (from Grid view) | `multipleLookupValues` | - | - |
| Discipline | `singleLineText` | - | - |
| Primary Contact | `singleLineText` | - | - |
| Contact Email | `singleLineText` | - | - |
| Contact Number | `phoneNumber` | - | - |
| Logo | `multipleAttachments` | - | - |
| Full Job List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| JOB NAME & NO Rollup (from Full Job List) | `rollup` | - | Rollup field: fldziPbYt7Hiozyup |
| Vendor Records | `multipleRecordLinks` | - | Links to: `tbl4yOMTINASBer7u` |
| Vendor Fees | `rollup` | - | Rollup field: fldD6C6cg4ZTyS45J |
| Amount Rollup (from Vendor Expense) | `rollup` | - | Rollup field: fldTotU55rYejyGr1 |
| Proposal Vendor Estimates | `multipleRecordLinks` | - | Links to: `tblId9pw2FVXForCH` |
| Vendor Expense | `multipleRecordLinks` | - | Links to: `tblflBK4iAsmcPSn8` |
| Project Vendors | `multipleRecordLinks` | - | Links to: `tbl4yOMTINASBer7u` |

### Views

- **Grid view** (`grid`)

---

## T05_Clients

**Table ID:** `tblIDEKXrdoetpFtG`  
**Primary Field:** fldaaPsy1BrBgs5AR  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Primary Contact | `singleLineText` | - | - |
| Primary Contact Email | `email` | - | - |
| Primary Contact Phone | `phoneNumber` | - | - |
| Full Job List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Logo | `multipleAttachments` | - | - |
| Website | `url` | - | - |
| Last Modified | `lastModifiedTime` | - | - |

### Views

- **Grid view** (`grid`)

---

## T06_Project Vendors

**Table ID:** `tbl4yOMTINASBer7u`  
**Primary Field:** fldGY4cMRztVyIHc3  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `formula` | Concatenates the job number and vendor name from their respective lookup fields. | Formula: `ARRAYJOIN({fld38UnuzP8eZcPW8}, " ") & " " & ARRAYJ...` |
| PROJECT | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| VENDOR | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |
| VENDOR COSTS | `currency` | - | Precision: 2 |
| VENDOR AHF % | `percent` | - | Precision: 0 |
| VENDOR AHF $ | `formula` | - | Formula: `{fldD6C6cg4ZTyS45J} * {flddaMk3mnevdb1ZZ}` |
| TOTAL VENDOR FEE | `formula` | - | Formula: `{fldD6C6cg4ZTyS45J} * (1 + {flddaMk3mnevdb1ZZ})` |
| Full_Job_List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| JOB NAME & NO (from PROJECT) | `multipleLookupValues` | - | - |
| JOB NO | `multipleLookupValues` | - | - |
| Name (from VENDOR) | `multipleLookupValues` | - | - |
| Vendors | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |

### Views

- **Grid view** (`grid`)

---

## T07_Vendor Expense

**Table ID:** `tblflBK4iAsmcPSn8`  
**Primary Field:** fldDolDOs4zV2Gm2S  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Expense ID | `autoNumber` | - | - |
| Invoice | `multipleRecordLinks` | - | Links to: `tblMjIpM1WYepdNCy` |
| Project Name & Number (from Invoice) | `multipleLookupValues` | - | - |
| Vendor | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |
| Name (from Vendor) | `multipleLookupValues` | - | - |
| Amount | `currency` | - | Precision: 2 |
| Description | `multilineText` | - | - |
| Vendor Expense Rollup (from Invoice) | `rollup` | - | Rollup field: fldVS8Rn1B5a1GVN2 |
| Vendors | `singleLineText` | - | - |
| Vendors 2 | `singleLineText` | - | - |
| Proposal Vendor Estimates | `multipleRecordLinks` | - | Links to: `tblId9pw2FVXForCH` |

### Views

- **Grid view** (`grid`)

---

## T08_Proposal Vendor Estimates

**Table ID:** `tblId9pw2FVXForCH`  
**Primary Field:** fldsiqeBdrl0vwkTW  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Estimate ID | `autoNumber` | - | - |
| Proposal | `multipleRecordLinks` | - | Links to: `tblsE6Uj4DyOXCkpl` |
| Vendor | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |
| Estimated Amount | `currency` | - | Precision: 2 |
| Service Description | `singleLineText` | - | - |
| Converted to Expense | `checkbox` | - | - |
| Linked Expense | `multipleRecordLinks` | - | Links to: `tblflBK4iAsmcPSn8` |
| Expense Variance | `formula` | - | Formula: `IF({fldFMVOi8i4PrN0JH}, {fldEtwTFA1x8Rts53} - {fld...` |
| Actual Amount | `multipleLookupValues` | - | - |
| Proposal Status | `multipleLookupValues` | - | - |
| Is Active | `formula` | - | Formula: `IF(AND({fldb2A5ixF15aqn28} = "Accepted", NOT({fldF...` |
| Convert to Expense | `singleLineText` | - | - |
| Vendor Name | `multipleLookupValues` | - | - |

### Views

- **Grid view** (`grid`)

---

## T09_Jurisdictions

**Table ID:** `tblPjNKI1SCRFUwYN`  
**Primary Field:** fldqs94doHmU0rWyc  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| File Managers | `multipleRecordLinks` | - | Links to: `tbl67ULST92raRDen` |
| Permit Types | `multipleRecordLinks` | - | Links to: `tblFFgwtMHveTZJPb` |
| Permit Applications | `multipleRecordLinks` | - | Links to: `tblICS7xCK0fyc3QC` |
| T01_Job_List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Province | `singleLineText` | - | - |
| Abb. | `singleLineText` | - | - |

### Views

- **Grid view** (`grid`)

---

## T10_Permit Types

**Table ID:** `tblFFgwtMHveTZJPb`  
**Primary Field:** flds9nE8XIK4ZJZfp  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Jurisdiction | `multipleRecordLinks` | - | Links to: `tblPjNKI1SCRFUwYN` |
| Permit Type | `singleSelect` | - | Choices: Development Permit, Building Permit, Business Licence |
| Permit Sub-Type | `singleSelect` | - | Choices: Exterior Changes, Change of Tenancy |
| Estimated Approval Time | `number` | In weeks | Precision: 1 |
| Permit Applications | `multipleRecordLinks` | - | Links to: `tblICS7xCK0fyc3QC` |

### Views

- **Grid view** (`grid`)

---

## T11_Permit Applications

**Table ID:** `tblICS7xCK0fyc3QC`  
**Primary Field:** fldebJ3Tfjt9uyKFQ  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Application ID | `formula` | - | Formula: `{fldPLYAWeBZnS7Qqf} & " - " & {fld1fcursoectqjxC}` |
| Permit Status | `singleSelect` | - | Choices: Submitted, Canceled, In Review, Standby for Documents, Approved |
| Permit Number | `singleLineText` | - | - |
| Additional Reference Numbers | `singleLineText` | - | - |
| Applicant | `multipleRecordLinks` | - | Links to: `tblZl5HNB9mhDIlHc` |
| Application Date | `date` | - | - |
| Anticipated Acceptance Date | `date` | - | - |
| Acceptance Date | `date` | - | - |
| Deficiencies | `multipleAttachments` | - | - |
| T01_Job_List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Permit Types | `multipleRecordLinks` | - | Links to: `tblFFgwtMHveTZJPb` |
| Jurisdictions | `multipleRecordLinks` | - | Links to: `tblPjNKI1SCRFUwYN` |
| Application Fee | `currency` | - | Precision: 2 |
| Fee Paid | `checkbox` | - | - |
| Date Paid | `date` | - | - |
| Fee Paid by Peake | `checkbox` | - | - |
| Fee is Disbursable | `checkbox` | - | - |
| Fee Invoice to Client | `formula` | - | Formula: `IF(AND({fldIS0Hma4SaHFgP9}, {fldXYPiC3t0NVHkg3}), ...` |
| Internal ID Prefix | `autoNumber` | - | - |

### Views

- **Grid view** (`grid`)

---

## T12_File Managers

**Table ID:** `tbl67ULST92raRDen`  
**Primary Field:** fldEcYPa47DQZv0aF  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Email | `email` | - | - |
| Phone Number | `phoneNumber` | - | - |
| Discipline | `singleSelect` | - | Choices: Mechanical, Electrical, Planning Services, Safety Codes, File Manager, Inspector - Safety Codes, Inspector - Mechanical, Inspector - Plumbing, Inspector - Electrical, Transportation, Waste Management, Urban Forestry |
| Jurisdiction | `multipleRecordLinks` | - | Links to: `tblPjNKI1SCRFUwYN` |
| Projects | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Helpful | `singleSelect` | - | Choices: Yes, No, Unknown, Neutral |
| Notes | `multilineText` | - | - |

### Views

- **Grid view** (`grid`)

---

## T13_Staff

**Table ID:** `tblZl5HNB9mhDIlHc`  
**Primary Field:** fldBZI4Oh1d9U9pvG  

**Description:** Linked table from Base B03

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| First Name | `singleLineText` | - | - |
| Employee ID | `number` | - | Precision: 0 |
| Last Name | `singleLineText` | - | - |
| Full Name | `multilineText` | - | - |
| Position | `singleSelect` | - | Choices: Senior Designer, Designer, Drafter, Junior Designer, Owner/Manager, Office Administrator |
| Department | `singleSelect` | - | Choices: Production, Management, Administration |
| Email | `singleLineText` | - | - |
| Phone | `singleLineText` | - | - |
| Hire Date | `date` | - | - |
| Employment Status | `singleSelect` | - | Choices: Active, On Leave, Terminated |
| Emergency Contact Name | `singleLineText` | - | - |
| Birthdate | `date` | - | - |
| Profile Photo | `multipleAttachments` | - | - |
| Notes | `multilineText` | - | - |
| Skills & Certifications | `singleLineText` | - | - |
| Staff Skills | `singleLineText` | - | - |
| Training & Development | `singleLineText` | - | - |
| Years with Company | `number` | - | Precision: 0 |
| Age | `number` | - | Precision: 0 |
| Total Trainings Attended | `number` | - | Precision: 0 |
| Most Recent Training Date | `date` | - | - |
| Monthly Recap | `singleLineText` | - | - |
| T01_Job_List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Project Count | `rollup` | - | Rollup field: fldziPbYt7Hiozyup |
| Hourly Rate | `currency` | - | Precision: 2 |
| Burdened Rate | `currency` | - | Precision: 2 |
| T01_Job_List copy | `singleLineText` | - | - |
| T11_Permit Applications | `multipleRecordLinks` | - | Links to: `tblICS7xCK0fyc3QC` |
| T02_Proposals | `multipleRecordLinks` | - | Links to: `tblsE6Uj4DyOXCkpl` |

### Views

- **Grid view** (`grid`)

---

## T14_Building Archive

**Table ID:** `tblFCpYX3EApt1Yhg`  
**Primary Field:** fldNEfaznJy39T3FO  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Building Address | `singleLineText` | - | - |
| Unit Address | `singleLineText` | - | - |
| Associated Projects | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Matterport | `checkbox` | - | - |
| Matterport Link | `url` | - | - |
| Base Building Drawings | `checkbox` | - | - |
| Renovation Drawings | `checkbox` | - | - |
| Revit Model | `checkbox` | - | - |
| Revit Version | `singleLineText` | - | - |
| Due Diligence Report | `checkbox` | - | - |

### Views

- **Grid view** (`grid`)

---

## T15_Contacts_Outdated

**Table ID:** `tbly6q8AulC8MpOjB`  
**Primary Field:** fldTAFJLV1XYakToY  

**Description:** Linked table from Base B06

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Full Name | `multilineText` | - | - |
| First Name | `singleLineText` | - | - |
| Middle Name | `multilineText` | - | - |
| Last Name | `multilineText` | - | - |
| Suffix | `multilineText` | - | - |
| Company | `multilineText` | - | - |
| Department | `multilineText` | - | - |
| Job Title | `multilineText` | - | - |
| Business Street | `multilineText` | - | - |
| Business Street 2 | `multilineText` | - | - |
| Business Street 3 | `multilineText` | - | - |
| Business City | `singleLineText` | - | - |
| Business State | `singleLineText` | - | - |
| Business Postal Code | `multilineText` | - | - |
| Business Country/Region | `singleSelect` | - | Choices: Canada, , United States of America, USA, Philippines, Alberta, T2G 0Y2, Australia |
| Home Street | `multilineText` | - | - |
| Home Street 2 | `multilineText` | - | - |
| Home Street 3 | `multilineText` | - | - |
| Home City | `multilineText` | - | - |
| Home State | `singleSelect` | - | Choices: , AB, BC, Alberta, 4B5, SK |
| Home Postal Code | `multilineText` | - | - |
| Home Country/Region | `multilineText` | - | - |
| Other Street | `multilineText` | - | - |
| Other Street 2 | `multilineText` | - | - |
| Other Street 3 | `multilineText` | - | - |
| Other City | `multilineText` | - | - |
| Other State | `multilineText` | - | - |
| Other Postal Code | `multilineText` | - | - |
| Other Country/Region | `singleSelect` | - | Choices: , United States of America, Canada |
| Assistant's Phone | `multilineText` | - | - |
| Business Fax | `multilineText` | - | - |
| Business Phone | `multilineText` | - | - |
| Business Phone 2 | `multilineText` | - | - |
| Callback | `multilineText` | - | - |
| Car Phone | `multilineText` | - | - |
| Company Main Phone | `multilineText` | - | - |
| Home Fax | `multilineText` | - | - |
| Home Phone | `multilineText` | - | - |
| Home Phone 2 | `multilineText` | - | - |
| ISDN | `multilineText` | - | - |
| Mobile Phone | `multilineText` | - | - |
| Other Fax | `multilineText` | - | - |
| Other Phone | `multilineText` | - | - |
| Pager | `multilineText` | - | - |
| Primary Phone | `multilineText` | - | - |
| Radio Phone | `multilineText` | - | - |
| TTY/TDD Phone | `singleSelect` | - | Choices: , +1 (800) 704-8656, +1 (877) 333-0433 |
| Telex | `multilineText` | - | - |
| Account | `multilineText` | - | - |
| Anniversary | `singleSelect` | - | Choices: 00-0-0, 2007-10-21 |
| Assistant's Name | `multilineText` | - | - |
| Billing Information | `multilineText` | - | - |
| Birthday | `singleSelect` | - | Choices: 00-0-0 |
| Business Address PO Box | `multilineText` | - | - |
| Categories | `singleSelect` | - | Choices: Client - Commercial, Builder - Commercial, Concrete - site work, Metal Fabricators, Audio/Video/Phone/Media, Drywall, Fireplaces, Utilities, Fencing, Exteriors, Government - Foothills County, Building Materials - Finishing, Government Alberta, Finishing Materials, Insulation, Flooring & Tile, Plumbing Fixtures, Granite & Marble & Stone, Milling, Roofing, Painters, Building Materials, Builder - Residential, Furniture, Client, Window Coverings, Mechanical, Building Movers, Building Materials - Hardware, Elevators, Excavators, Masonry & Glass Block, Restaurant, Landscape, HVAC, Green Venders, Inspectors, Fabrics, Water Wells, Artists & Galleries, Client - Prospect, Client - Builder, Electrical, Equipment Supplier, Metal Siding & Roofing, Lighting, Masonry & Glass Block;Stucco, HVAC;Plumbing & Heating, Windows, Design Professionals, Millwork shop, Government - Calgary, Delivery, Transportation, Computer, Landscape;Masonry & Glass Block;Transportation, Land Surveyor & Locators, Carpenters - Handyman, Accounting, Educators, Photographer, Equipment Repair, Interior Designers, Printing, , Home Media, Restaurant Suppliers, Cleaning, Builder - Renovations, Consultants - Lighting Design, IT, Flowers, Glass, Hotel & B&B, Insurance, Barnwood, Office, Consultants - Building Code, Engineers - Envelope, ER VENDOR;Landscape Contractors, ER VENDOR;Flooring & Tile, Building Materials - deck & fence, Real Estate, Plumbing & Heating;HVAC, Automation & Lighting & Controls, Language Translation Service, Organizations, Builder - Timber Frame, Warehouse Racking, Metal Products, Building Materials - paint, Employee - Current, Condo Nieghbors, Engineers Structural, Office;Office Cleaning, Client - Property Owners & Managers, Employee - past, Metal Fabricators;Blacksmith, Catering, WDHouse vendor;Fire Protection, WDHouse vendor;Metal Fabricators, WDHouse vendor;Automation & Lighting & Controls, WDHouse vendor;Engineer - glass, Consultant - Land Development, Architects, Recruitment, Acoustics, Mechanical;WDHouse vendor;HVAC, Flooring & Tile;WDHouse vendor, Client Landscape, Lawyers, Landscape Architect, Electronics Recycling, Associations, Data Wiring, Glass;ER VENDOR, ER VENDOR;Glass, Building Materials - specialty, Stairs;WDHouse vendor, Moving & Storage, WDHouse vendor;Granite & Marble & Stone, Granite & Marble & Stone;WDHouse vendor, Mechanical;Plumbing & Heating, Building Materials - Masony, WDHouse vendor;Sandblasting, Building Materials - Doors, Makeup Artist, Engineers - Electrical, Engineers - Mechanical, Engineers - Civil, Consultant - Hydronics, Employee Benefits Plans, SHP Vendor;Builder - Commercial, Builder - Residential - BC, Building Materials - Insulated Panels, Office Furniture, Building Materials - trusses, Developer, Human Resources, Consultants - Prefab, Interiors, Locksmith, Reproduction, Surveyors, Overhead Doors, Builder - Modular Homes, Client - Resort, Interior Designers;Real Estate, Meat, Consultants - Spec Writer, Metal Fabricators;Welding, Pre-Fab Panels, Renderers, Employee - Betterpros, HVAC;Mechanical;Plumbing & Heating, Builder - ICF, ENCabin vendor, Building Inspections, Client - Church, ENCabin vendor;Timber Frames, Marketing, WDHouse vendor;Mechanical, Overhead Doors;WDHouse vendor, Mechanical;WDHouse vendor, Engineers Fire Protection, Landscape Architect;ENCabin vendor, Consultants - Energy Code, Computer;Vendor, Landscape Contractors, Concrete - pre-cast;WDHouse vendor, Metal Fabricators;WDHouse vendor, WDHouse vendor;Engineer - concrete anchorage, Engineers Lighting;WDHouse vendor, WDHouse vendor;Consultants - Lighting Design, Consultants - Land Development, Government - Strathmore, Engineers Environmental, WDHouse vendor;Exteriors, Real Estate;ENCabin vendor, Government - Chestermere, Fire Protection;WDHouse vendor, Water Treatment;ENCabin vendor, Landscape Architect;WDHouse vendor, Plumbing & Heating;WDHouse vendor, WDHouse vendor;Lighting, Client ER, Roofing;WDHouse vendor, WDHouse vendor;Stairs, Water Treatment, Radon, Fire Protection, Septic Systems, Government - Strathcona County, Overhead Cranes, Engineers Fire Hazard Analyst, Stairs, Conveyance Systems, Metal Fabricators;Exteriors, Engineers Acoustics, Pools & Spas, Windows;Window Coverings, Building Materials - Architectural pre-cast, Glass;Windows;SHP Vendor, HVAC;SHP Vendor, Plumbing Fixtures;SHP Vendor, Building Materials  - Exterior, Engineers Geotechnical, Kitchen - Supplier, Kitchen - Supplier;SHP Vendor, Timber Frames, Building Materials - ICF, Masonry & Glass Block;WDHouse vendor, Metal Fabricators;Metal Siding & Roofing, Software, Windows;Builder - Commercial, Engineering - Materials Testing, Plumbing & Heating, Building Materials - stairs, Consultant - BIM, Consultants - Compliance Specialist, Building Materials - steel joists, Building Materials - Comm Doors & HW, Inspirational Resource, Roofing;Metal Siding & Roofing;Exterior Finish, Roofing;Exterior Finish;Metal Siding & Roofing, Client Restaurant, Steel Structures;Builder - Commercial, Builder - Commercial;Steel Structures, Steel Structures, Building Operator/Services, Recycling - electronics, Government - Revelstoke, Drone, Building Materials - timber, Paving, Landscape Contractors;Landscape Architect, Plumbing & Heating;ER VENDOR;Window Coverings;Windows, Upholstry, Flooring & Tile;Granite & Marble & Stone, Client School, Roofing;Insulation, Government - High River, Signs, Builder - Commercial;Solar, Consultants - Building Envelope, Exterior Finish;Exteriors, Kitchen - Supplier;Masonry & Glass Block, Millwork shop;Kitchen - Supplier, Printing;Marketing, Carpenters, Consultants - Roofing, Metal Fabricators;Metal Products;Metal Siding & Roofing;Exteriors, Glass;Windows, Exterior Finish, ER VENDOR, Government - Rocky View County, Government - Regional District of East Kootenay, Millwork shop;ER VENDOR, Flooring & Tile;ER VENDOR, HVAC;Fireplaces, Insurance;Inspectors, Greenhouses, Arborist, Consultants - Accessibility, Wine, Engineers Water, Client;Landscape Contractors, Leather, Consultants - Contract Admin, Engineers Consulting, Septic Systems;Paving, Government - Cochrane, Engineers - Structural;Engineers Structural, Government - Okotoks, Kitchen - commercial designer, Waste Management, Asbestos Abatement, Restaurant Suppliers;Kitchen - Supplier, Roofing;Exteriors, Foam Products, Client;Property Managers, Landscape;Landscape Contractors, Buildings - Post Frame, Consultants - Feng Shui, Stucco, Insulation;Marketing, Aquariums, Hardware, Solar, Screw Piles, Engineers Lighting, Appliances, Millwork shop;Condo Nieghbors, Antiques, Green Roof;Roofing, Consultant - Security, Green Venders;Mechanical, Condo Nieghbors;Land Surveyor & Locators, Garden, Client;Photographer, Flooring & Tile;Masonry & Glass Block, Real Estate;Client, Building Materials;Stairs, Building Materials;Window Coverings, Client;Fencing, Green Venders;Plumbing Fixtures, WDHouse vendor, Builder - Residential;Builder - Renovations, Client Commercial;Builder - Commercial, Builder - Renovations;Client Prospect, Fire Restoration, Fire Stopping, Staff Prospect, WDHouse vendor;Automobile, Consultant - steel detailing, Client Commercial;Office Furniture, Building Materials - Laminates;Building Materials  - Exterior, Consultants - Drafting, Client - Residential, Family, Concrete - specialties, Engineers - Structural, Building Materials - Laminates, Government - Canada, Consultant - work safety, Financial services, Client - Residential;Client Commercial, Crane Service, Building Materials - wood |
| Children | `multilineText` | - | - |
| Directory Server | `multilineText` | - | - |
| E-mail Address | `multilineText` | - | - |
| E-mail Type | `singleSelect` | - | Choices: SMTP, , EX |
| E-mail Display Name | `multilineText` | - | - |
| E-mail 2 Address | `multilineText` | - | - |
| E-mail 2 Type | `singleSelect` | - | Choices: , SMTP, EX |
| E-mail 2 Display Name | `multilineText` | - | - |
| E-mail 3 Address | `multilineText` | - | - |
| E-mail 3 Type | `singleSelect` | - | Choices: , SMTP |
| E-mail 3 Display Name | `multilineText` | - | - |
| Gender | `singleSelect` | - | Choices: Unspecified |
| Government ID Number | `multilineText` | - | - |
| Hobby | `multilineText` | - | - |
| Home Address PO Box | `multilineText` | - | - |
| Initials | `singleSelect` | - | Choices: H.T., A.H., T.A., D.B., L.B., V.B., J.B., M.B., A.B., R.B., R.V., M.C., G.K.C., C.C., D.C., R.C., W.D., J.D., C.V.D., M.M.D., G.E., L.E., W.F., J.F., M.G., L.G., T.G., R.H., J.H., S.H., D.H., P.H., T.I., G.S.J., J.P., A.J., G.B.K., R.K., J.L., S.L., , B.M., S.M., K.M., D.M., R.M., C.N., L.P., C.P., D.P., R.R., D.R., G.S., M.W.S., T.S., S.S., R.S., D.S., J.T., M.V., R.W.W., E., M.T., T.B., J.E., R.J.D.G., D.G., R.R.B.L., L.W., K.S.B.S., J., T.J., C.H.A.H., E.T., B.W., C.F., R.D., W.A., S.G., H.F., D.W., A.G.S., S.A., L.C., M.F., F.V.H., L.H., R.Y., A.R., C.R., J.M., R.v.W., E.C., C.S., M.S., M.K., K.S., T.W., I.D., B.F., T.e., D.E., I.E.E., M.D., B.D., K.D., P.N., R.O., K.G., C.B., S., L.O., O.D., N.M., S.T., T.L., K.L., P.B., J.C., J.W., F.M., S.F., C.V.Y., G.M., D.N., P.S.D., D.L., K.J.S., V., A.I., W.T., C.D., E.P., M.H., S.D., L., B.S., P.S., T., B.B., G.H., P.R., T.T., A.F., M.J., K.F., B.A., B.C., R.P., S.B., K., D.A., J.Y., T.D.J., D.T., W.D.J., K.N., S.R., R.M.J., R.F., J.G., S.K., A.M., K.W., B., M.L., B.H., A.A., N.B., L.L., C.W., G.G., G.C., G.R., P.D., C.T., E.S., R.L., M.M.T.T., E.K., S.N., L.S., P.T., C.A., G.K., J.S., B.J., S.P., D.V., T.O., K.O., H.C., D.D., M.P., K.H., A.D., K.C., O.O., B.G., M.O., P.V., R.J., M., N.H., V.F., N.P., E.B., A.V., C.H., B.K., G.B., N., B.V., A.Q., G.Z., T.N., N.O., W.B., M.R., M.W., S.C., J.C.B., D.O., L.M., G.D., T.Y., A., B.Z., R.C.H.H.R., M.M., T.R., A.K., C.M., H.R., D.K., B.P., E.A., B.R., C.K., T.K., O.L., T.C., T.H., W.I., R., M.Y., R.W., S.E., A.G., G.N., B.v.R., P.M., G.Q., J.J., L.K., J.A., S.W., T.U., N.S., E.L., Z.R., W.V.G., N.K., E.G., A.E., J.N., W.G., B.L., K.B., P.W., A.C., D., T.P., G.P., P.L., P.C., S.O., 4.B., J.R., R.G., L.J., D.J., A.P., J.O., N.v.D., N.O.W., G.L., K.U., K.K., P.A., T.M., E.R., G.W., N.R., K.P., L.V., M.K.T., R.A., K.Z., W.M., L.F., C., M.N., D.F., P., I.O., A.L., R.E., Z.J., P.F., A.S., N.C., C.V., B.E., G.I., N.P.G.M., H.S., P.G., C.G., H.D., W.C.J., R.U., F.J., H.E., H.A., V.C., L.R., C.R.M., B.T., L.A., N.S.K., C.L., F.D., K.A., I.M., G.A., W.E., A.c., I.S., R.N., V.M., S.P.P., J.K., T.P.G., M.A., S.J., T.D., L.L.M., W.W., B.W.M., K.V., F.Z., B.T.D., B.Q., s.m., F.A., N.T., J.C.G., P.O., E.E., A.O., W.P., J.Z., C.O., P.R.H., R.K.P., S.Z., H.M., H.L., K.R., E.W., W.S., P.K., A.W., M.A.M.D., M.E., D.L.Y., A.A.C., N.G., E.N., K.T., E.E.S., P.J., D.F.K.F., W., F.B., B.N., D.C.J.M., T.E., J.J.G., C.C.T., W.C., W.N., J.G.M., W.K., J.V., E.J.J.R., E.D., R.Q., K.I., V.K., P.E., J.F.K., J.I., H.H., P.D.B., M.S.B., G.J.L., V.H., M.D.V., N.W., R.S.B., E.H., G.S.M., N.S.D., I.G., N.E., C.M.G., R.D.C., G.T., K.Y., N.L.M., A.N., W.J., C.E., N.D.P., C.J., D.D.S., Y.K., E.J.A., N.L., A.L.B., V.G., L.D., M.K.C.D., N.a.D.D., B.L.F., B.O., a.M.B., G.M.A., R.H.C., G.J., F.G., A.T., A.B.R., B.U., A.C.S., N.J., T.L.K., C.D.C., A.P.B., R.C.S., V.B.P., V.N., N.A., B.B.S., B.H...S.S., C.Z., J.A.T., J.P.S., M.J.K., G.E.J., M.V.B., N.F., K.P.W., T.V.D., V.P., I.P., P.F.N., R.A.M., L.D.Y., D.G.L., B.D.L., J.A.H., L.J.G., T.F., M.D.C., D.B.M., J.L.B., K.J.B., F.C., T.V., F.W., A.V.B., F.P., J.D.E., F.N., M.Z., T.Z., H.G., F.L., E.C.H., P.V.D.C., C.D.O.D., R.B.c. |
| Internet Free Busy | `multilineText` | - | - |
| Keywords | `multilineText` | - | - |
| Language | `multilineText` | - | - |
| Location | `multilineText` | - | - |
| Manager's Name | `multilineText` | - | - |
| Mileage | `multilineText` | - | - |
| Notes | `multilineText` | - | - |
| Office Location | `multilineText` | - | - |
| Organizational ID Number | `multilineText` | - | - |
| Other Address PO Box | `multilineText` | - | - |
| Priority | `singleSelect` | - | Choices: Normal |
| Private | `multilineText` | - | - |
| Profession | `multilineText` | - | - |
| Referred By | `multilineText` | - | - |
| Sensitivity | `singleSelect` | - | Choices: Normal |
| Spouse | `multilineText` | - | - |
| User 1 | `multilineText` | - | - |
| User 2 | `multilineText` | - | - |
| User 3 | `multilineText` | - | - |
| User 4 | `multilineText` | - | - |
| Web Page | `multilineText` | - | - |
| T04_Vendors | `multipleRecordLinks` | - | Links to: `tblKxbn935QbK2OrM` |
| Role | `singleSelect` | - | Choices: Commercial Broker, Commercial GC, Principal |
| T01_Job_List | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| T01_Job_List 2 | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| T01_Job_List 3 | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |

### Views

- **Grid view** (`grid`)

---

## T16_Matterport

**Table ID:** `tblWCIhvThgROHJQ7`  
**Primary Field:** fldLHje7kMgn6OzPi  

**Description:** Linked table from Base B07

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `multilineText` | - | - |
| T05_Job List | `singleLineText` | - | - |
| Related Project | `multipleRecordLinks` | - | Links to: `tbl6eilFaVl5XOT8x` |
| Scan Time (Total) | `duration` | - | - |
| Scanner copy | `singleLineText` | - | - |
| Billable Scan Fee | `currency` | - | Precision: 2 |
| Total Square Footage | `number` | - | Precision: 1 |
| Includes Exterior | `checkbox` | - | - |
| Scan Date | `date` | - | - |
| Tour URL | `url` | - | - |

### Views

- **Grid view** (`grid`)

---

## T17_KPIs

**Table ID:** `tblHiy7l6d2HGhKC4`  
**Primary Field:** fldWGcYTeitf7OSrR  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Notes | `multilineText` | - | - |
| Assignee | `singleCollaborator` | - | - |
| Status | `singleSelect` | - | Choices: Todo, In progress, Done |
| Attachments | `multipleAttachments` | - | - |
| Attachment Summary | `aiText` | An AI generated summary of the Attachments field. Upload files to Attachments to generate a summary. | - |

### Views

- **Grid view** (`grid`)

---

## Grid view

**Table ID:** `tbloG35ODDW8RrhhP`  
**Primary Field:** fldGRAjBaP9TxPs29  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Link Id | `multilineText` | - | - |
| Building | `singleLineText` | - | - |
| Building Id | `singleLineText` | - | - |
| Associated Job | `singleLineText` | - | - |
| T01_Building List | `singleLineText` | - | - |

### Views

- **Grid view** (`grid`)

---

## T15_Contacts

**Table ID:** `tblLxxbtgDCTbK8Jo`  
**Primary Field:** fldjLqPGZ0sWlUMrT  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Full Name | `multilineText` | - | - |
| Title | `multilineText` | - | - |
| Company | `multilineText` | - | - |
| Department | `multilineText` | - | - |
| Job Title | `multilineText` | - | - |
| Business Phone | `multilineText` | - | - |
| Home Phone | `multilineText` | - | - |
| Mobile Phone | `multilineText` | - | - |
| E-mail Address | `multilineText` | - | - |
| T0.2_Companies | `multipleRecordLinks` | - | Links to: `tblRs5VjTvn0xJA8c` |

### Views

- **Grid view** (`grid`)

---

## Grid view 3

**Table ID:** `tblRs5VjTvn0xJA8c`  
**Primary Field:** fldpnj9vufn4bmn94  

### Fields

| Field Name | Type | Description | Options |
|------------|------|-------------|---------|
| Name | `singleLineText` | - | - |
| Employees | `multipleRecordLinks` | - | Links to: `tblLxxbtgDCTbK8Jo` |
| Logo | `multipleAttachments` | - | - |

### Views

- **Grid view** (`grid`)

---

## Relationships

### Entity Relationship Diagram

```mermaid
erDiagram
    T01_Job_List ||--o{ T13_Staff : "Project Lead"
    T01_Job_List ||--o{ T05_Clients : "Clients"
    T01_Job_List ||--o{ T04_Vendors : "Vendors"
    T01_Job_List ||--o{ T03_Invoices : "Invoices"
    T01_Job_List ||--o{ T06_Project Vendors : "Project Vendors"
    T01_Job_List ||--o{ T06_Project Vendors : "PRJT VNDRS"
    T01_Job_List ||--o{ T12_File Managers : "File Managers"
    T01_Job_List ||--o{ T02_Proposals : "T02_Proposals"
    T01_Job_List ||--o{ T11_Permit Applications : "Permit Applications"
    T01_Job_List ||--o{ T09_Jurisdictions : "Jurisdiction"
    T01_Job_List ||--o{ T01_Job_List : "PRIOR PROJECT"
    T01_Job_List ||--o{ T01_Job_List : "From field: PRIOR PROJECT"
    T01_Job_List ||--o{ T14_Building Archive : "T14_Building Archive"
    T01_Job_List ||--o{ T16_Matterport : "T16_Matterport"
    T01_Job_List ||--o{ T15_Contacts_Outdated : "PROJECT BUILDER"
    T01_Job_List ||--o{ T15_Contacts_Outdated : "PROJECT BROKER"
    T01_Job_List ||--o{ T15_Contacts_Outdated : "REFERRAL FROM"
    T02_Proposals ||--o{ T01_Job_List : "Job"
    T02_Proposals ||--o{ T08_Proposal Vendor Estimates : "Proposal Vendor Estimates"
    T02_Proposals ||--o{ T13_Staff : "Prepared By"
    T03_Invoices ||--o{ T01_Job_List : "Job"
    T03_Invoices ||--o{ T07_Vendor Expense : "Vendor Expense"
    T04_Vendors ||--o{ T15_Contacts_Outdated : "Grid view"
    T04_Vendors ||--o{ T01_Job_List : "Full Job List"
    T04_Vendors ||--o{ T06_Project Vendors : "Vendor Records"
    T04_Vendors ||--o{ T08_Proposal Vendor Estimates : "Proposal Vendor Estimates"
    T04_Vendors ||--o{ T07_Vendor Expense : "Vendor Expense"
    T04_Vendors ||--o{ T06_Project Vendors : "Project Vendors"
    T05_Clients ||--o{ T01_Job_List : "Full Job List"
    T06_Project Vendors ||--o{ T01_Job_List : "PROJECT"
    T06_Project Vendors ||--o{ T04_Vendors : "VENDOR"
    T06_Project Vendors ||--o{ T01_Job_List : "Full_Job_List"
    T06_Project Vendors ||--o{ T04_Vendors : "Vendors"
    T07_Vendor Expense ||--o{ T03_Invoices : "Invoice"
    T07_Vendor Expense ||--o{ T04_Vendors : "Vendor"
    T07_Vendor Expense ||--o{ T08_Proposal Vendor Estimates : "Proposal Vendor Estimates"
    T08_Proposal Vendor Estimates ||--o{ T02_Proposals : "Proposal"
    T08_Proposal Vendor Estimates ||--o{ T04_Vendors : "Vendor"
    T08_Proposal Vendor Estimates ||--o{ T07_Vendor Expense : "Linked Expense"
    T09_Jurisdictions ||--o{ T12_File Managers : "File Managers"
    T09_Jurisdictions ||--o{ T10_Permit Types : "Permit Types"
    T09_Jurisdictions ||--o{ T11_Permit Applications : "Permit Applications"
    T09_Jurisdictions ||--o{ T01_Job_List : "T01_Job_List"
    T10_Permit Types ||--o{ T09_Jurisdictions : "Jurisdiction"
    T10_Permit Types ||--o{ T11_Permit Applications : "Permit Applications"
    T11_Permit Applications ||--o{ T13_Staff : "Applicant"
    T11_Permit Applications ||--o{ T01_Job_List : "T01_Job_List"
    T11_Permit Applications ||--o{ T10_Permit Types : "Permit Types"
    T11_Permit Applications ||--o{ T09_Jurisdictions : "Jurisdictions"
    T12_File Managers ||--o{ T09_Jurisdictions : "Jurisdiction"
    T12_File Managers ||--o{ T01_Job_List : "Projects"
    T13_Staff ||--o{ T01_Job_List : "T01_Job_List"
    T13_Staff ||--o{ T11_Permit Applications : "T11_Permit Applications"
    T13_Staff ||--o{ T02_Proposals : "T02_Proposals"
    T14_Building Archive ||--o{ T01_Job_List : "Associated Projects"
    T15_Contacts_Outdated ||--o{ T04_Vendors : "T04_Vendors"
    T15_Contacts_Outdated ||--o{ T01_Job_List : "T01_Job_List"
    T15_Contacts_Outdated ||--o{ T01_Job_List : "T01_Job_List 2"
    T15_Contacts_Outdated ||--o{ T01_Job_List : "T01_Job_List 3"
    T16_Matterport ||--o{ T01_Job_List : "Related Project"
    T15_Contacts ||--o{ Grid view 3 : "T0.2_Companies"
    Grid view 3 ||--o{ T15_Contacts : "Employees"
```

### Relationship Details

| From Table | Field | To Table | Type |
|------------|-------|----------|------|
| T01_Job_List | Project Lead | T13_Staff | many-to-one |
| T01_Job_List | Clients | T05_Clients | many-to-one |
| T01_Job_List | Vendors | T04_Vendors | many-to-many |
| T01_Job_List | Invoices | T03_Invoices | many-to-many |
| T01_Job_List | Project Vendors | T06_Project Vendors | many-to-many |
| T01_Job_List | PRJT VNDRS | T06_Project Vendors | many-to-many |
| T01_Job_List | File Managers | T12_File Managers | many-to-many |
| T01_Job_List | T02_Proposals | T02_Proposals | many-to-many |
| T01_Job_List | Permit Applications | T11_Permit Applications | many-to-many |
| T01_Job_List | Jurisdiction | T09_Jurisdictions | many-to-many |
| T01_Job_List | PRIOR PROJECT | T01_Job_List | many-to-many |
| T01_Job_List | From field: PRIOR PROJECT | T01_Job_List | many-to-many |
| T01_Job_List | T14_Building Archive | T14_Building Archive | many-to-many |
| T01_Job_List | T16_Matterport | T16_Matterport | many-to-many |
| T01_Job_List | PROJECT BUILDER | T15_Contacts_Outdated | many-to-many |
| T01_Job_List | PROJECT BROKER | T15_Contacts_Outdated | many-to-many |
| T01_Job_List | REFERRAL FROM | T15_Contacts_Outdated | many-to-one |
| T02_Proposals | Job | T01_Job_List | many-to-one |
| T02_Proposals | Proposal Vendor Estimates | T08_Proposal Vendor Estimates | many-to-many |
| T02_Proposals | Prepared By | T13_Staff | many-to-one |
| T03_Invoices | Job | T01_Job_List | many-to-one |
| T03_Invoices | Vendor Expense | T07_Vendor Expense | many-to-many |
| T04_Vendors | Grid view | T15_Contacts_Outdated | many-to-many |
| T04_Vendors | Full Job List | T01_Job_List | many-to-many |
| T04_Vendors | Vendor Records | T06_Project Vendors | many-to-many |
| T04_Vendors | Proposal Vendor Estimates | T08_Proposal Vendor Estimates | many-to-many |
| T04_Vendors | Vendor Expense | T07_Vendor Expense | many-to-many |
| T04_Vendors | Project Vendors | T06_Project Vendors | many-to-many |
| T05_Clients | Full Job List | T01_Job_List | many-to-many |
| T06_Project Vendors | PROJECT | T01_Job_List | many-to-one |
| T06_Project Vendors | VENDOR | T04_Vendors | many-to-one |
| T06_Project Vendors | Full_Job_List | T01_Job_List | many-to-many |
| T06_Project Vendors | Vendors | T04_Vendors | many-to-many |
| T07_Vendor Expense | Invoice | T03_Invoices | many-to-one |
| T07_Vendor Expense | Vendor | T04_Vendors | many-to-one |
| T07_Vendor Expense | Proposal Vendor Estimates | T08_Proposal Vendor Estimates | many-to-many |
| T08_Proposal Vendor Estimates | Proposal | T02_Proposals | many-to-one |
| T08_Proposal Vendor Estimates | Vendor | T04_Vendors | many-to-one |
| T08_Proposal Vendor Estimates | Linked Expense | T07_Vendor Expense | many-to-one |
| T09_Jurisdictions | File Managers | T12_File Managers | many-to-many |
| T09_Jurisdictions | Permit Types | T10_Permit Types | many-to-many |
| T09_Jurisdictions | Permit Applications | T11_Permit Applications | many-to-many |
| T09_Jurisdictions | T01_Job_List | T01_Job_List | many-to-many |
| T10_Permit Types | Jurisdiction | T09_Jurisdictions | many-to-one |
| T10_Permit Types | Permit Applications | T11_Permit Applications | many-to-many |
| T11_Permit Applications | Applicant | T13_Staff | many-to-one |
| T11_Permit Applications | T01_Job_List | T01_Job_List | many-to-one |
| T11_Permit Applications | Permit Types | T10_Permit Types | many-to-many |
| T11_Permit Applications | Jurisdictions | T09_Jurisdictions | many-to-many |
| T12_File Managers | Jurisdiction | T09_Jurisdictions | many-to-many |
| T12_File Managers | Projects | T01_Job_List | many-to-many |
| T13_Staff | T01_Job_List | T01_Job_List | many-to-many |
| T13_Staff | T11_Permit Applications | T11_Permit Applications | many-to-many |
| T13_Staff | T02_Proposals | T02_Proposals | many-to-many |
| T14_Building Archive | Associated Projects | T01_Job_List | many-to-many |
| T15_Contacts_Outdated | T04_Vendors | T04_Vendors | many-to-many |
| T15_Contacts_Outdated | T01_Job_List | T01_Job_List | many-to-many |
| T15_Contacts_Outdated | T01_Job_List 2 | T01_Job_List | many-to-many |
| T15_Contacts_Outdated | T01_Job_List 3 | T01_Job_List | many-to-many |
| T16_Matterport | Related Project | T01_Job_List | many-to-many |
| T15_Contacts | T0.2_Companies | Grid view 3 | many-to-many |
| Grid view 3 | Employees | T15_Contacts | many-to-many |

