# Power-BI
18. How do you optimize DAX calculations for performance?
•	Strategies:
1.	Avoid iterators like SUMX, FILTER, unless necessary. Instead, use simple aggregators (SUM, AVERAGE).
2.	Replace calculated columns with measures for better performance.
3.	Use variables (VAR) to store intermediate calculations, reducing redundant work.
4.	Minimize the use of row context, which is more resource-intensive.
•	Example:
Instead of writing:
DAX
TotalProfit = SUMX(Sales, Sales[Revenue] - Sales[Cost])

Use:
DAX
TotalProfit = SUM(Sales[Revenue]) - SUM(Sales[Cost])

19. What is query folding, and why is it important?
•	Query Folding: This is the process where Power Query sends data transformation requests back to the source system (e.g., SQL database), so the source handles the heavy lifting.
•	Importance:
o	Reduces Data Transfer: Only the necessary data is transferred to Power BI.
o	Improves Refresh Performance: The source system processes the data, reducing the time Power BI takes to load it.
o	Efficient Resource Usage: It leverages the source system's power rather than doing all transformations in Power BI.
•	Example:
If you're working with a large SQL database, instead of pulling all rows into Power BI and filtering them, Power Query pushes the filter to the SQL database, which reduces the amount of data being loaded into Power BI.

20. How do you manage schema changes in Power BI?
•	Strategies:
1.	Use Lineage View in Power BI to track data dependencies.
2.	Monitor schema changes (like column or table renames) in the source system.
3.	Update Power Query steps if columns or tables are renamed.
4.	Use version control (like Git) to back up dataset versions.
•	Example:
If your data source changes column names, you’ll need to go into Power Query and update the steps to reflect those changes to avoid errors.
