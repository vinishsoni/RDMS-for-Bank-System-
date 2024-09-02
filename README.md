# RDMS for Bank 

In this assignment, we embark on a journey to create a comprehensive database management
system for a fictional bank. This project aims to equip us with the skills to design and implement
a robust MySQL database, execute both basic and complex SQL queries, and apply theoretical
concepts such as the CAP theorem within the practical context of a dynamic banking system.

## Our Bank System:

Our imaginary bank, "BSBI Bank," is a modern financial institution committed to delivering
seamless and secure banking experiences to its diverse customer base. The bank offers a range of
services, including various account types, loan facilities, and personalized financial solutions. To
efficiently manage its operations, BSBI Bank has decided to implement a sophisticated database
system that captures and organizes crucial information about customers, accounts, transactions,
employees, branches, and loans.

### Entities in Our Database:

1. Customer: Represents individuals who hold accounts with the bank. Each customer has a unique
identifier, name, and contact information.
2. Account: Reflects the various types of accounts offered by the bank, such as savings or
checking. Each account is associated with a specific customer and holds details like balance and
account type.
3. Transaction: Records the financial activities of customers, including deposits, withdrawals, and
transfers. Each transaction is linked to a particular account.
4. Employee: Signifies the staff members working within the bank. Each employee has a unique
ID, name, role, and contact information.
5. Branch: Represents the physical locations of the bank. Each branch has a unique identifier,
location, and contact information.
6. Loan: Manages information related to loans provided by the bank. This includes details like loan
amount, interest rate, repayment status, and the associated customer.

### ER Diagram: 

Below is an Entity-Relationship (ER) diagram for the BSBI bank system, including SQL table
definitions, entity descriptions, and relationships. In this representation, Foreign Keys (FK) are
excluded for simplicity.

Entities and Attributes:
1. Customer:
Attributes: CustomerID (PK), Name, ContactInfo
2. Account:
Attributes: AccountNumber (PK), Balance, Type, CustomerID
3. Transaction:
Attributes: TransactionID (PK), Type, Amount, Date, AccountNumber
4. Employee:
Attributes: EmployeeID (PK), Name, Role, ContactInfo
5. Branch:
Attributes: BranchID (PK), Location, ContactInfo
6. Loan:
Attributes: LoanID (PK), Amount, InterestRate, RepaymentStatus, CustomerID

### Relationships:
● Customer - Account (One-to-Many): A customer can have multiple accounts, but an
account belongs to one customer.

● Account - Transaction (One-to-Many): An account can have multiple transactions, but a
transaction is associated with one account.

● Employee - Branch (One-to-Many): An employee works at one branch, but a branch can
have multiple employees.

● Customer - Loan (One-to-Many): A customer can have multiple loans, but a loan is
associated with one customer.

![Screenshot (897)](https://github.com/user-attachments/assets/5556b907-73f9-496c-b163-93808381f70f)

### MySQL Implementation

Creating schemas involves defining the structure of the tables, including primary and foreign keys. Below is the SQL code for creating the tables with foreign key relationships.

![Screenshot (894)](https://github.com/user-attachments/assets/6dfd8379-3b89-497a-8a14-77303bf510a3)

![Screenshot (896)](https://github.com/user-attachments/assets/455fa2b7-df7f-4e2c-b164-868b0607a2f8)

![Screenshot (895)](https://github.com/user-attachments/assets/537940ad-ca67-4104-89c5-59dc9a4e310d)

### Performing Queries on Database:

Let us now perform some queries on this database for a better understanding of SQL functions.

1. View Transaction History Grouped by Transaction Type:
 The bank wants to analyze transaction history, categorizing transactions by type.

![28 01 2024_11 34 34_REC](https://github.com/user-attachments/assets/79a0ca81-532b-4d9f-a869-0c22db8fe8fb)


2. Check Account Balance and Group by Account Type:
 The bank manager wants to check the total balance for each account type.

![28 01 2024_11 36 07_REC](https://github.com/user-attachments/assets/ed6ce71c-e2a3-48a9-b515-7e40de068b5d)


3. View Transaction History:
 A customer wants to view their recent transactions.

![28 01 2024_11 38 41_REC](https://github.com/user-attachments/assets/6a7c51f7-0199-4bf6-9e07-c2dd7c83ffcc)


4. List Employees and Their Branches:
 The bank manager wants a list of all employees and the branches they work at.

![28 01 2024_11 41 50_REC](https://github.com/user-attachments/assets/9a5ed764-9170-4130-8416-e220bcb96b6e)


5. Total Balance Across Accounts:
 The bank manager wants to know the total balance across all accounts.

![28 01 2024_15 17 02_REC](https://github.com/user-attachments/assets/e8f53e4b-3954-4022-a68f-d6b3f3b4ab3e)


6. Find Customers with Active Loans:
 The bank wants to identify customers with active loans.

![28 01 2024_11 47 22_REC](https://github.com/user-attachments/assets/dc21ae6f-7527-48b1-9a9b-ed7cfd0db177)

7. Transactions in a Specific Date Range:
 The bank wants to audit transactions within a specific date range.

![28 01 2024_11 49 09_REC](https://github.com/user-attachments/assets/22f97358-e3c3-456a-b084-1bda25a28ca6)


8. Analyzing Loan Distribution Across Customer Segments:
 The bank aims to analyze the distribution of loans across different customer segments based on their total account balances. This analysis will help identify whether high-value customers tend to have more significant loan amounts.

![28 01 2024_12 04 16_REC](https://github.com/user-attachments/assets/a2197276-5c11-44f1-9dbb-2bc01b0bcce9)


### Importance of CAP Theorm:

A basic framework for comprehending the trade-offs in distributed system design is provided by Eric Brewer's CAP theorem. A distributed system cannot concurrently accomplish all three of the following guarantees, according to the theorem: Partition Tolerance, Availability, and Consistency. Because of this, system architects have to be very selective about which mix of these guarantees best fits the objectives and unique requirements of their application.

●Consistency (C): In the context of the CAP theorem, consistency refers to the shared view of data that is simultaneously available to every node in a distributed system. A consistent system will reflect the most recent writing in any read operation that comes after a write operation. Especially in applications like financial systems where data accuracy is critical, achieving consistency is essential.

●Availability (A): The capacity of the system to respond to requests for information without ensuring that the response includes the most recent version of the data is known as availability. Users can communicate with the system in highly available systems even when certain nodes are momentarily unavailable or experiencing problems. In situations like internet services and e-commerce platforms, where continuous servicing is vital, availability is crucial.

●Partition Tolerance (P): The capacity of a system to function in the event of a network partition, which may result in node communication failures, is known as partition tolerance. A network that is partition-tolerant can be split into separate pieces, and each section of the system will be able to operate independently of the others. This is especially crucial for systems that are spread across several data centres or geographical areas where network outages are possible.



### Banking System with CAP Theorem

Maintaining uniformity in a banking system is essential to guaranteeing that all account balances are precise and current. Customers must be available in order to view their account information and complete transactions. Because distributed systems are susceptible to network outages or delays, partition tolerance is required.
Consistency (C): The system makes sure that all nodes' balances are updated correctly when a customer starts a financial transfer between two accounts. Regardless of the node, the most recent committed transaction is reflected in all ensuing read operations.
Availability (A): Users should be able to access their account details and complete transactions even in the event that a temporary network outage renders some nodes in the distributed system inaccessible. Requests from users are still handled by the system.
Partition Tolerance (P): In the event that there are transient network partitions between some of its nodes, the banking system keeps running without interruption. The system remains available overall, and transactions can still be completed.

In this case, the banking system maintains partition tolerance while giving priority to availability and consistency. It might, however, momentarily forego consistency during network splits in order to preserve availability.
For example, the system may let read operations even if they do not represent the most recent updates in the event of a network partition, when some nodes are cut off from the main network (giving off a bit of consistency for availability). The system attempts to reconcile the data and restore complete consistency after the network partition is fixed.

To sum up, the CAP theorem compels system designers to deliberate about trade-offs according to the particular requirements of their applications. For example, during network partitions, a financial system may prioritise availability and consistency at the expense of some consistency. Comprehending and managing these trade-offs is essential for constructing reliable and effective decentralised systems that fulfil the demands of practical uses.




