# BLS-data-finder
Using Python to access Bureau of Labor Statistics data via public API

### **Addressing a common pain point:**

The data analysis and reporting I perform throughout the course of a semester frequently requires me to reference datapoints from a specific year. Throughout my research workflow, accessing specific data points -- i.e. the labor union membership rate for a particular year --  can be a clunky process given the nature of working with government databases and sheer volume of information at hand.

### **Solution:**

This Python function references specific series IDs from the Bureau of Labor Statistics (BLS) and returns the corresponding datapoints from each series for a user-inputted year.

## **Summary of function sections:**

#### **1. Library Imports**
- requests: used for making HTTP requests to the BLS API
- json: used to parse JSON data
- pandas: used for organizing and displaying the data in a DataFrame format
- Ipython.display: used for displaying the DataFrame in Google Colab or Jupyter

#### **2. Function Definition (get_bls_stats)**
- Takes the year to fetch the data, with optional to_csv and filename arguments for exporting the data to the CSV

#### **3. Series IDs Dictionary**
- Contains mapping between descriptive labels and their corresponding BLS series IDs. This defines the specific data points to be retrieved from the BLS API

#### **4. API Request**
- Sends a POST request to the BLS API with the required parameters (series IDs, start year, end year). It checks for successful stats code (200) to ensure the request is valid.

#### **5. Extract and Process Results**
- Iterates over the response data, extracting values for each series, calculating the average, and storing the results in the dictionary
- **NOTE:** There is no month data available for the series used in the function, only annual data. The average calculation has no impact on the output. However, the function _is_ set up to accomodate series with month data with a few tweaks, if desired (see in-line annotation)

#### **6. Create and Display DataFrame**
- Converts the results into a pandas.DataFrame, formats the colunms, and sorts them by metric name. The DataFrame is displayed using IPython.display

#### **7. CSV Export (Optional)**
- If to_csv=True and a valid filename is provided, the DataFrame is exported as a CSV file
