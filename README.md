# Network Analysis for Money Laundering Detection
### Author: Virendrasinh Chavda

<p align="justify">
This repository contains the code and analysis for detecting suspicious transactions and accounts involved in money laundering using **network analysis**. The project explores how centrality measures, community detection algorithms, and visualization techniques can identify key players in fraudulent networks. 
</p>

## Table of Contents
1. [Overview](#Overview)
2. [Data](#Data)
3. [Methodology](#Methodology)
4. [Results](#Results)
5. [Future Work](#Future-Work)
6. [Contributing](#Contributing)
7. [License](#License)

## Overview
Money laundering is a sophisticated financial crime where illicit funds are disguised as legitimate. Traditional rule-based detection methods struggle with evolving and complex laundering schemes. In this project, we use **network analysis** techniques to detect money laundering by identifying central and suspicious nodes (accounts) in transaction networks. Centrality measures like **degree**, **closeness**, and **betweenness centrality** help uncover significant nodes. Additionally, community detection algorithms such as the **Girvan-Newman algorithm** are employed to isolate suspicious clusters of accounts.

This project focuses on identifying key nodes and their roles in money laundering networks based on transaction patterns in a synthetic banking dataset. The project applies network analysis concepts to visualize and analyze suspicious activities, which can be further integrated with machine learning for predictive modeling.

## Data:
The dataset used for this project is sourced from the [IBM AMLSim Dataset](https://www.kaggle.com/datasets/anshankul/ibm-amlsim-example-dataset), which simulates real-world banking transactions. It consists of 1.32 million transaction records with attributes like:

* **TX_ID**: Transaction ID
* **SENDER_ACCOUNT_ID**: The sender's account number
* **RECEIVER_ACCOUNT_ID**: The receiver's account number
* **TX_AMOUNT**: The amount of the transaction
* **IS_FRAUD**: A binary label indicating whether the transaction is fraudulent

For the purposes of this project, a subset of 2000 transactions was sampled and used for analysis due to computational constraints. Columns related to transaction type, timestamp, and fraud labels were excluded, focusing on **network properties**.

## Methodology:
### 1. Preprocessing
The dataset was preprocessed by:

* Grouping transactions from the same accounts and aggregating them to form a more manageable network.
* Renaming columns: **SENDER_ACCOUNT_ID** as **SOURCE** and **RECEIVER_ACCOUNT_ID** as **TARGET**.
* Aggregating transaction data to calculate the total transaction count and total **transaction amount** between pairs of accounts.

### 2. Network Construction
A directed network graph was created using the processed transaction data:

* **Nodes** represent accounts, and edges represent transactions between these accounts.
* Network visualization was generated to display the flow of transactions and the structure of relationships between accounts.

### 3. Centrality Measures
The following centrality measures were calculated to identify important nodes (accounts):

* **Degree Centrality**: Measures the number of transactions linked to an account.
* **Closeness Centrality**: Identifies how quickly an account can access other accounts in the network.
* **Betweenness Centrality**: Detects nodes that act as intermediaries in the flow of transactions.

### 4.Community Detection
The **Girvan-Newman algorithm** was applied to identify clusters of nodes that form communities within the transaction network. These communities were analyzed to determine if any suspicious nodes (e.g., high centrality scores) were present.

### 5. Visualisation
* A **degree distribution plot** was generated to identify accounts with significantly higher transaction activity.
* **Communities** were highlighted with different colors, and key nodes (based on centrality) were visualized within these communities to observe their potential roles in money laundering schemes.

## Results:

* **Key Nodes**: Nodes with high degree, closeness, and betweenness centrality were identified as potential collectors or intermediaries in laundering schemes. For example, Node 9993 was found to be a collector within a community, having a high degree and acting as a hub for incoming transactions.
* **Communities**: The network was split into several communities, with certain nodes playing dominant roles in these clusters. These nodes were flagged as suspicious due to their centrality within the community.
* **Network Analysis Effectiveness**: Network analysis techniques effectively highlighted nodes that could be of interest for further investigation, indicating that these methods can complement traditional rule-based or machine learning approaches in anti-money laundering efforts.

## Future Work:
* **Integration with Machine Learning**: Centrality and community detection results can be used as features in a machine learning model to predict fraudulent accounts.
* **Expanding the Dataset**: The analysis can be expanded to include the full dataset for more comprehensive insights.
* **Feature Addition**: Incorporating additional account information such as account type, ownership, and geographical location could improve the identification of suspicious accounts.

## Contributing

Contributions are welcome! If you would like to suggest improvements, report issues, or contribute to the project, feel free to open a pull request or submit an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

For more details, please refer to the [project report](./Money-Laundering-Report.pdf).
