# Conundrum 2: Holiday Hoodies
Check Out the [Tableau Dashboard](https://public.tableau.com/app/profile/michael.r.thompson/viz/Conundrum2Dataiku/Conundrum2?publish=yes)
Ask Questions in the [Dataiku Forums](https://community.dataiku.com/t5/Community-Conundrums/Conundrum-2-Holiday-Hoodies/m-p/5634/thread-id/7/highlight/false)
## Problem Statement
The second Conundrum is here!

A company has separate datasets for the 2016 and 2015 numbers and needs to compare a subset of 2016’s numbers with the numbers from 2015.

Given the two datasets "orders_2015" and "orders_2016", create a single visualization that answers the question, "Did we sell more Hoodies in 2016 than in 2015 in the first 25 days of December?"

Good luck - I hear there are stacks of clever ways to go about it!

## Plugins to Install
1. [Tableau Hyper Format](https://www.dataiku.com/product/plugins/tableau-hyper-export): Allow syou to export your flow to a Tableau extract

## Solution Details: by Zone in Project
#### Import Data
1. Imported CSV files and unioned together (Years 2015 with 2016)

#### Tableau
1. Inserting "Prepare" recipe in case I want to clean the data prior to exporting to Tableau
2. Inserted "Export to Folder" recipe to export using the ["Tableau Hyper Format" plugin](https://www.dataiku.com/product/plugins/tableau-hyper-export)
3. Selected "Other exports"
4. Selected "Upload to Tableau Server (Hyper)" under "Exporters"
5. Completed connection details
6. Outside of the flow, connected to Tableau extract file

#### Dataiku
1. Inserted a "Sync" recipe to simply create a branch of the same datasource with a different name
2. Opened the data source
3. Opened the "Charts" tab
4. Used the native Dataiku to visualize the data

** I have added comments throughout the project flow to help you understand what steps I accomplished in more detail
