# Network Analysis for Money Laundering Detection
### Author: Virendrasinh Chavda

<p align="justify">
This repository contains the code and analysis for detecting suspicious transactions and accounts involved in money laundering using <strong>network analysis</strong>. The project explores how centrality measures, community detection algorithms, and visualization techniques can identify key players in fraudulent networks. 
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
<p align="justify">
Money laundering is a sophisticated financial crime where illicit funds are disguised as legitimate. Traditional rule-based detection methods struggle with evolving and complex laundering schemes. In this project, we use <strong>network analysis</strong> techniques to detect money laundering by identifying central and suspicious nodes (accounts) in transaction networks. Centrality measures like <strong>degree</strong>, <strong>closeness</strong>, and <strong>betweenness centrality</strong> help uncover significant nodes. Additionally, community detection algorithms such as the <strong>Girvan-Newman algorithm</strong> are employed to isolate suspicious clusters of accounts.
</p>

<p align="justify">
This project focuses on identifying key nodes and their roles in money laundering networks based on transaction patterns in a synthetic banking dataset. The project applies network analysis concepts to visualize and analyze suspicious activities, which can be further integrated with machine learning for predictive modeling.
</p>

## Data:
<p align="justify">
The dataset used for this project is sourced from the [IBM AMLSim Dataset](https://www.kaggle.com/datasets/anshankul/ibm-amlsim-example-dataset), which simulates real-world banking transactions. It consists of 1.32 million transaction records with attributes like:
</p>

* <strong>TX_ID</strong>: Transaction ID
* <strong>SENDER_ACCOUNT_ID</strong>: The sender's account number
* <strong>RECEIVER_ACCOUNT_ID</strong>: The receiver's account number
* <strong>TX_AMOUNT</strong>: The amount of the transaction
* <strong>IS_FRAUD</strong>: A binary label indicating whether the transaction is fraudulent

<p align="justify">
For the purposes of this project, a subset of 2000 transactions was sampled and used for analysis due to computational constraints. Columns related to transaction type, timestamp, and fraud labels were excluded, focusing on <strong>network properties</strong>.
</p>

## Methodology:
### 1. Preprocessing
<p align="justify">
The dataset was preprocessed by:

* Grouping transactions from the same accounts and aggregating them to form a more manageable network.
* Renaming columns: <strong>SENDER_ACCOUNT_ID</strong> as <strong>SOURCE</strong> and <strong>RECEIVER_ACCOUNT_ID</strong> as <strong>TARGET</strong>.
* Aggregating transaction data to calculate the total transaction count and total <strong>transaction amount</strong> between pairs of accounts.
</p>

### 2. Network Construction
<p align="justify">
A directed network graph was created using the processed transaction data:

* <strong>Nodes</strong> represent accounts, and edges represent transactions between these accounts.
* Network visualization was generated to display the flow of transactions and the structure of relationships between accounts.
</p>

### 3. Centrality Measures
<p align="justify">
The following centrality measures were calculated to identify important nodes (accounts):

* <strong>Degree Centrality</strong>: Measures the number of transactions linked to an account.
* <strong>Closeness Centrality</strong>: Identifies how quickly an account can access other accounts in the network.
* <strong>Betweenness Centrality</strong>: Detects nodes that act as intermediaries in the flow of transactions.
</p>
  
### 4.Community Detection
<p align="justify">
The <strong>Girvan-Newman algorithm</strong> was applied to identify clusters of nodes that form communities within the transaction network. These communities were analyzed to determine if any suspicious nodes (e.g., high centrality scores) were present.
</p>

### 5. Visualisation
<p align="justify">
* A <strong>degree distribution plot</strong> was generated to identify accounts with significantly higher transaction activity.
* <strong>Communities</strong> were highlighted with different colors, and key nodes (based on centrality) were visualized within these communities to observe their potential roles in money laundering schemes.
</p>

## Results:
<p align="justify">
* <strong>Key Nodes</strong>: Nodes with high degree, closeness, and betweenness centrality were identified as potential collectors or intermediaries in laundering schemes. For example, Node 9993 was found to be a collector within a community, having a high degree and acting as a hub for incoming transactions.
* <strong>Communities</strong>: The network was split into several communities, with certain nodes playing dominant roles in these clusters. These nodes were flagged as suspicious due to their centrality within the community.
* <strong>Network Analysis Effectiveness</strong>: Network analysis techniques effectively highlighted nodes that could be of interest for further investigation, indicating that these methods can complement traditional rule-based or machine learning approaches in anti-money laundering efforts.
</p>

## Future Work:
<p align="justify">
* <strong>Integration with Machine Learning</strong>: Centrality and community detection results can be used as features in a machine learning model to predict fraudulent accounts.
* <strong>Expanding the Dataset</strong>: The analysis can be expanded to include the full dataset for more comprehensive insights.
* <strong>Feature Addition</strong>: Incorporating additional account information such as account type, ownership, and geographical location could improve the identification of suspicious accounts.
</p>

## Contributing
<p align="justify">
Contributions are welcome! If you would like to suggest improvements, report issues, or contribute to the project, feel free to open a pull request or submit an issue.
</p>

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

For more details, please refer to the [project report](./Money-Laundering-Report.pdf).
