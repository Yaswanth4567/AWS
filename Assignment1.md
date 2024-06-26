**1.What is OLTP and OLAP**

Online Transaction Processing, or OLTP for short, entails handling and executing massive amounts of transactions in real time. Its speed and frequency of use are optimised for tasks like adding, updating, and removing data from databases.

Online Analytical Processing, or OLAP for short, is the process of evaluating vast amounts of data to make decisions. It entails utilising multidimensional structures like cubes and data warehouses for querying, reporting, and data analysis in order to obtain insights.

**2.Difference between OLTP and OLAP**

Purpose:
OLTP: Primarily focused on transactional operations, such as inserting, updating, and deleting data. Its goal is to ensure data integrity and support day-to-day operations.
OLAP: Geared towards analytical operations, such as querying, reporting, and analysing data to support decision-making processes.
Data Structure:
OLTP: Typically uses a normalised data model optimised for transaction processing, minimising redundancy and ensuring data consistency.
OLAP: Often employs a denormalized or dimensional data model, including data cubes and star or snowflake schemas, to facilitate efficient querying and analysis.
Workload:
OLTP: Handles a high volume of short and simple transactions, often involving individual data records.
OLAP: Processes complex queries involving aggregations, calculations, and comparisons across large datasets.
Response Time:
OLTP: Requires fast response times to support real-time transaction processing, often in milliseconds or seconds.
OLAP: Tolerates longer response times, as the focus is on analytical tasks rather than immediate transaction processing. Response times can range from seconds to minutes, depending on the complexity of the query and the volume of data.
Concurrency:
OLTP: Designed to handle concurrent transactions from multiple users or applications, often using techniques like locking to maintain data consistency.
OLAP: Typically involves fewer concurrent users and transactions compared to OLTP systems, with a focus on supporting decision-makers and analysts rather than simultaneous transaction processing.
Indexes and Optimization:
OLTP: Relies heavily on indexes and optimization techniques to ensure fast access and manipulation of individual records.
OLAP: Emphasises pre-aggregation, indexing, and other optimization strategies to improve query performance for complex analytical queries.
Overall, OLTP and OLAP serve different purposes and have distinct characteristics tailored to the needs of transaction processing and data analysis, respectively.


**3.Database Normal Forms**


Database normalisation is a technique used to organise the structure of a relational database to minimise redundancy and dependency. There are five normal forms, each building upon the previous one to eliminate various types of data anomalies:

First Normal Form (1NF):
Ensures that each column in a table contains atomic (indivisible) values and that there are no repeating groups of columns.
Example: Breaking down a column containing multiple values into separate rows (e.g., splitting a "Phone Numbers" column into individual "Phone Number" rows).

Second Normal Form (2NF):
Builds on 1NF and ensures that all non-key attributes are fully functionally dependent on the primary key.
In simpler terms, it removes partial dependencies by moving attributes that depend on only part of the primary key to a separate table.
Example: Splitting a table into two tables to eliminate partial dependencies.

Third Normal Form (3NF):
Builds on 2NF and ensures that there are no transitive dependencies, meaning that non-key attributes are not dependent on other non-key attributes.
It removes transitive dependencies by moving attributes dependent on other non-key attributes to separate tables.
Example: Splitting a table to eliminate attributes that are functionally dependent on non-key attributes.

Boyce-Codd Normal Form (BCNF):
A stricter form of 3NF where every determinant (attribute whose value determines another attribute) is a candidate key.
It ensures that there are no non-trivial functional dependencies where a determinant determines a non-prime attribute.
Example: Ensuring that each determinant uniquely determines all other attributes in the table.

Fourth Normal Form (4NF):
Addresses multivalued dependencies, where an attribute set can have multiple values for another attribute set.
It involves splitting tables to remove multivalued dependencies and store them in separate tables.
Example: Breaking down a table with multivalued dependencies into multiple tables to eliminate redundancy.
These normal forms help ensure database integrity, reduce redundancy, and facilitate efficient data management and querying.


     
**4.Dimension vs Fact Table**

Dimension:
Dimension tables contain descriptive attributes that provide context and characteristics for the data stored in a data warehouse or data mart.
They are typically denormalized and have a primary key that uniquely identifies each dimension record.
Dimension tables are often smaller in size compared to fact tables.
Example dimensions include time, geography, product, customer, etc.

Fact Table:
Fact tables contain quantitative measures or metrics (facts) and foreign keys that reference dimension tables.
They represent the core data that is being analysed in a data warehouse and are usually much larger in size compared to dimension tables.
Fact tables often have additive, semi-additive, or non-additive measures.
Examples of measures in a fact table include sales amount, quantity sold, profit, etc.

Types of Dimensions:

Conformed Dimension:
A dimension that is shared and consistent across multiple fact tables within the same data warehouse or across multiple data marts.
Conformed dimensions ensure consistency and enable integration and comparison of data across different parts of the organisation.
Degenerate Dimension:
A dimension that exists in the fact table itself rather than being represented by a separate dimension table.
Degenerate dimensions are typically attributes that are part of the fact's primary key but do not have their own separate table.
Slowly Changing Dimension (SCD):
A dimension that changes over time but at a relatively slow rate.
There are different types of slowly changing dimensions, including Type 1 (overwrite old data), Type 2 (add new rows with new data), and Type 3 (add new columns to record changes).
Junk Dimension:
A dimension composed of flags, indicators, or other non-descriptive attributes that do not fit well into existing dimensions.
Junk dimensions help reduce the number of joins in queries by consolidating rarely used attributes into a single dimension table.
Role-Playing Dimension:
A dimension that is used in multiple contexts within the same fact table.
For example, a "Date" dimension may be used to represent different dates such as order date, ship date, and delivery date within the same fact table.
Understanding and properly designing dimension and fact tables, as well as the types of dimensions, is crucial for building effective data warehousing solutions that support analysis and decision-making.

**5.Snowflake vs star schema**

Snowflake and star schemas are both dimensional modelling techniques used in data warehousing to organise and structure data for analysis.Here's a comparison between the two:

Star Schema:

In a star schema, there is one central fact table surrounded by multiple dimension tables.
The fact table contains quantitative measures or metrics, while the dimension tables contain descriptive attributes that provide context for the measures.
Dimension tables are directly connected to the fact table through foreign key relationships.
It has a simple and denormalized structure, which makes it easy to understand and query.
Star schemas are well-suited for simple and straightforward analytical queries and are often preferred for their simplicity and performance.

Snowflake Schema:

In a snowflake schema, dimension tables are normalised into multiple related tables instead of being denormalized.
Dimension tables are further decomposed into sub-dimensions, creating a hierarchical structure.
This results in a more complex schema with multiple levels of relationships between tables.
Snowflake schemas reduce data redundancy and can be more efficient in terms of storage space, especially for large dimensions with repetitive data.
However, they can be more complex to understand and query compared to star schemas, as they require additional joins to retrieve data from multiple tables.

Comparison:

Complexity: Star schemas are simpler and easier to understand compared to snowflake schemas, which can be more complex due to normalisation.
Performance: Star schemas often offer better query performance because they involve fewer joins compared to snowflake schemas.
Storage: Snowflake schemas can save storage space by eliminating redundant data through normalisation, but they may require more joins to retrieve data, which can impact performance.
Flexibility: Star schemas are more flexible and easier to modify because of their denormalized structure, while snowflake schemas may require more effort to make changes due to normalisation.
In summary, star schemas are preferred for their simplicity, query performance, and ease of understanding, while snowflake schemas may be chosen for their storage efficiency and normalisation benefits, especially in scenarios with large and repetitive dimension data. The choice between the two depends on the specific requirements and trade-offs of the data warehousing project.





