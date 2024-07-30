# Data-Science-Thesis
Repo for all code and data associated with my Data Science Thesis 2024.
#

# 1. Get_The_Data.ipynb
    1.1 Gets a list of products that have ever had a fund switch.
    1.2 Use this list of products to get the full population of policies that can possibly switch funds.
    1.3 Create the file \Full_Population.csv

    2.1 Get all Paxus fund switches
    2.2 Get all iSuite fund switches
    2.3 Map cobes to Products
    2.4 Merge the Paxus and iSuite fund switches.
    2.5 Create the file \All_Switches.csv

# 2. Get_The_Total_Fund_Switch_Population.ipynb
    2.1 Read the file \Full_Population.csv and clean the data.
    2.2 Create a dataframe to count the number of switchable policies per month.
    2.3 Read the file \All_Switches.csv and clean the data.
    2.4 Create a dataframe to count the number of switches per month.
    2.5 Merge the full population counts with the switch counts.
    2.6 Create the file \Horizon_Switch_Counts.csv
    
# 3. Analyse_Fund_Switch_Data.ipynb
    3.1 Read the switchable funds/switch counts file \Horizon_Switch_Counts.csv
    3.2 Look at the distribution of the data.
    3.3 Found a spike in fund switches.  Analysis shows that this is downw to a fund closure on those dates
        
# 4. Fix_the_Closed_Funds_Problem.ipynb
    4.1 Read back the dataset of all switches.
    4.2 Create a new dataframe with switches for the fund close date range.
    4.3 Get a list of policies that were involved in a fund closure.
    4.4 Using the policy numbers from the list of policies that were involved in a fund closure, create a list of switches to delete.
    4.5 Delete the fund closure switches.
    4.6 Create a dataframe with all other dates, outside teh fund closure period.
    4.7 Merge them back to get a dataframe that has the full set of switches, MINUS switches for policies involved in the fund closure.
    4.8 # 8. Re-sort by policy number and processing date and write out file \All_Switches_Without_Fund_Close.csv
    4.9 Get the switchable funds/switch counts.
    4.10 Create the Fund Switch Count dataframe.
    4.11 Drop duplicate policy numbers.
    4.12 recount - Not working on the recount.  I edited the file myself to continue.

# 5. Re-Analyse_Fund_Switch_Data.ipynb
 
# 6. Calculate_Historical_Fund_Switches.ipynb
    6.1 Get all switchable policies
    6.2 Filter to only take rows since 2020.
    6.3 Set the dates for historical switches.
    6.4 Get all fund switch records.
    6.5 Filter to only take rows since 2020.
    6.6 Merge the full population with the switches to create the prediction dataset.
    6.7 Add the comparable past switch dates for comparison.
    6.8 No significant past fund switch activity indicating potential future switches so no need to proceed.

# Get supplementary policy features. Switch data has been sourced and analysed so now supplement the data with various features identified in the thesis.
This builds towards a dataset which will be split.  One portion to be used in the training and evaluaio of the ML model an the other to run the prediction.
  
# 7. Get_Tax_Fee_and_Risk_Attributes.ipynb 
    7.1 Get tax attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a distribution that may help prediction/classification.
    7.2 Get policy feeattributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a distribution that may help prediction/classification.
    7.3 Get risk attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a distribution that may help prediction/classification.

# 8. Get_Asset_Attributes.ipynb.
    8.1 Get fund asset attributes as potential prodective features.  
    8.2 Tests the distribution of all features and only keeps ones with a distribution that may help prediction/classification.

# 9. Get_Premium_Attributes.ipynb.
    9.1 Get premium and premiun indexationattributes as potential prodective features.  
    9.2 Tests the distribution of all features and only keeps ones with a distribution that may help prediction/classification.

# 10. Get_Broker_Attributes.ipynb.
    10.1 Get broker attributes.
    10.2 Get commission attributes.
    10.3 Test the distribution of all features and only keeps ones with a distribution that may help prediction/classification.
    
# 11. Get_Client_Attributes.ipynb.
    11.1 Get client attributes as potential prodective features.  
    11.2 Get address information as potential prodective features.
    11.3 Get market segmentation data as potential prodective features.
    11.4 Test the distribution of all features and only keeps ones with a distribution that may help prediction/classification.
    
# 12. Customer_And_Policy_Attributes.ipynb.
    12.1 Merges all of the data to product a final file that, after synthesisation, will be loaded into the Data Robot catalog.
