# Dataset Extraction from Pubmed Central

# Project Overview
This repository contains a Python-based script designed to retrieve and scrape detailed article data from PubMed Central (PMC). The script automates the process of fetching PMC articles related to a given query, extracting relevant article information (such as titles, links, and article types), and saving this data in a structured format for further analysis. The project also checks for the availability of supplementary datasets within the articles and includes them in the final output.
The project is designed for users who need to collect academic article data for research, data analysis, or other purposes. The final output is saved into a CSV file, making it easy to manipulate and filter based on the user’s requirements.

# How Does This Script Work?
1. Fetch Article IDs:
Queries PubMed Central’s API to fetch PMC IDs related to a specific search term.
Supports fetching multiple articles with pagination, ensuring that up to 500 articles can be retrieved for each query.

2. Fetch Article Details:
Uses the PMC API to retrieve detailed metadata for each article ID, including the article’s title, publication type, and a direct link to the article.
The script can handle up to 100 articles per batch, making it efficient for large-scale retrieval.

3. Supplementary Material Check:
For each article, the script checks for the availability of supplementary datasets and includes the links to these datasets in the final output.
Supplementary materials, such as datasets or media files, are fetched and included as additional information.

4.  Save to CSV:
After retrieving and parsing the article details, the script saves the information into a CSV file.
The output CSV contains the title, link, article type, and supplementary datasets for each article.
Additionally, the script filters out articles without supplementary datasets and saves them to a separate CSV file for further analysis.

# Methodology
1. Fetching Article Data:
The script uses PubMed Central's Entrez Programming Utilities (E-utilities) to search for and retrieve relevant articles. A combination of esearch (to find article IDs) and efetch (to retrieve article metadata) API endpoints are used.

2. XML Parsing:
The script parses the XML response from the PubMed Central API using Python’s built-in xml.etree.ElementTree (ET) library to extract the necessary article details.

3. CSV Output:
The data is organized and written to a CSV file using pandas, with a filter applied to create a separate file for articles containing supplementary datasets.

![image](https://github.com/user-attachments/assets/3d7af304-a215-4de7-a03a-48140bc5683a)


# Challenges Faced and Solutions
1. Handling API Rate Limits:

Problem: The PubMed Central API imposes rate limits, and repeated requests may fail due to throttling.

Solution: Implemented retry logic and added delay between requests to avoid exceeding the API’s rate limits.

2. Parsing Supplementary Datasets:

Problem: Not all articles contain supplementary datasets, and parsing these required additional checks.

Solution: The script includes functions that specifically look for and retrieve supplementary materials, ensuring they are correctly captured and stored.

3. Batch Processing for Efficiency:

Problem: Fetching details for a large number of articles could slow down performance.

Solution: Implemented batch processing to handle articles in chunks of 100, making it more efficient when dealing with large data sets.

# Key Features
1. Efficient Article Retrieval: The script retrieves up to 500 articles per query using pagination and batch processing for faster results.
2. Comprehensive Data Extraction: Extracts key details, including titles, links, and supplementary datasets.
3. Customizable Queries: Allows users to input custom search queries, making the tool flexible for various research needs.
4. CSV Export: Outputs the results to easy-to-use CSV files, including a filtered CSV with articles that contain supplementary materials.
