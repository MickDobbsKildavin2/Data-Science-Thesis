# Data-Science-Thesis
 1. Get_The_Data.ipynb
    1.1 Gets a list of products that have ever had a fund switch.
    1.2 Use this list of products to get the full population of policies that can possibly switch funds.
    1.3 Create the file \Full_Population.csv

    2.1 Get all Paxus fund switches
    2.2 Get all iSuite fund switches
    2.3 Map cobes to Products
    2.4 Merge the Paxus and iSuite fund switches.
    2.5 Create the file \All_Switches.csv

 2. Get_The_Total_Fund_Switch_Population.ipynb
    2.1 Read the file \Full_Population.csv and clean the data.
    2.2 Create a dataframe to count the number of switchable policies per month.
    2.3 Read the file \All_Switches.csv and clean the data.
    2.4 Create a dataframe to count the number of switches per month.
    2.5 Merge the full population counts with the switch counts.
    2.6 Create the file \Horizon_Switch_Counts.csv
    
 3. Analyse_Fund_Switch_Data.ipynb
    3.1 Read the switchable funds/switch counts file \Horizon_Switch_Counts.csv
    3.2 Look at the distribution of the data.
    3.3 Found a spike in fund switches.  Analysis shows that this is downw to a fund closure on those dates
        
 4. Fix_the_Closed_Funds_Problem.ipynb
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

 5. Re-Analyse_Fund_Switch_Data.ipynb
    5.1 Look again at the distribution of teh switches.
     
 6. Calculate_Historical_Fund_Switches.ipynb
    6.1 Get all switchable policies
    6.2 Filter to only take rows since 2020.
    6.3 Set the dates for historical switches.
    6.4 Get all fund switch records.
    6.5 Filter to only take rows since 2020.
    6.6 Merge the full population with the switches to create the prediction dataset.
    6.7 Add the comparable past switch dates for comparison.
    6.8 No significant past fund switch activity indicating potential future switches so no need to proceed.

7. Get supplementary policy features. Switch data has been sourced and analysed so now supplement the data with various features identified in the thesis.
   This builds towards a dataset which will be split.  One portion to be used in the training and evaluaio of the ML model an the other to run the prediction.
   7.1 Get_Tax_Fee_and_Risk_Attributes.ipynb - Get tax, policy fee and risk attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a
       distribution that may help prediction/classification.
   7.2 Get_Asset_Attributes.ipynb- Get fund asset attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a distribution that may help 
       prediction/classification.
   7.3 Get_Premium_Attributes.ipynb- Get premium and premiun indexation attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a
       distribution that may help prediction/classification.
   7.4 Get_Broker_Attributes.ipynb - Get broker and commission attributes as potential prodective features.  Tests the distribution of all features and only keeps ones with a distribution 
       that may help prediction/classification.
   7.5 Get_Client_Attributes.ipynb - Get client attributes, address information and market segmentation data as potential prodective features.  Tests the distribution of all features and 
       only keeps ones with a distribution that may help prediction/classification.
   7.6 Customer_And_Policy_Attributes.ipynb - Merges all of the data to product a final file that, after synthesisation, will be loaded into the Data Robot catalog.

8. Get_Market_Index_Data.ipynb
   8.1 Get Market indices.
   8.2 Get the Equity indices.
   8.3 Get some corresponding Futuress indices.
   8.4 Get the ETFs.
   8.5 Get the Bond indices.
   8.6 Get the Commodities indices.
   8.7 Get the Currencies indices.
   8.8 Get the Volatility indices.
   8.9 Merge all dataframes.
   8.10 Plot the data.

9. Synthesise tha data.
   9.1 Synthesise_Full_Horizon_Tranche1.ipynb. For the first half of the data, use SDV to:
       - Generate single table metadata from the dataframe.
       - Auto detect metadata.
       - Create a synthesizer. 
          - Set enforce_min_max_values to ensure the synthetic data adheres to the min/max boundaries set by the real data.  
          - Use enforce_rounding to ensure rounding is not enforced.  The Age column is not rounded.
       - Use the fit method to train an ML model on the data. 
          - The synthesizer uses Gaussian Copulas to learn  distribution of the real data. This happens in two stages.  
          - It learns the distribution of each individual column (the marginal distribution).
          - The get_learned_distributions shows  the marginal distributions learned by the model to estimate the shape of each column.  
          - It outputs a dictionary that maps the name of each learned column to the distribution that estimates its shape.
       - Save the synthesizer as a pickle file to use on the real data, to generate synthetic data.
       - Create the synthetic data from the synthesiser.
       - Save the syntheised data to file.
   9.2 Synthesise_Full_Horizon_Tranche2.ipynb. For the second half of the data, use SDV to:
       - Reload the metadata.
       - Reload the Synthesizer pickle file.
       - Create the synthetic data from the synthesiser.
       - Save the syntheised data to file.
   9.3 Merge_Synthesised_Tranches.ipynb. 
       - The internal PII and commercially sensitive data was synthesised in 2 separate tranches because of memory constraibts. 
       - This python file merges them and this data is fully shareable because the synthesisation (code shared, data cannot) has obfuscated the original PII data.
       - This keeps the statistical integrity of the original data.
       - Mergesof the synthesised internal data with the fully shareable external data.
   9.2 Evaluate_Synthesised_Data.ipynb.
       - Read the full file.
       - Look at the distribution of the target variable.