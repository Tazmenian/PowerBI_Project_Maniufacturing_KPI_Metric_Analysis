# Project Title
Quantitative Analysis of Manufacturing KPI Metrics

## Description
This project involves analyzing production data to derive Key Performance Indicators (KPIs) that help assess and improve the quality and efficiency of the manufacturing process.

## Data
The dataset includes fields such as:
- **Name**: Operator's name
- **Date**: Production date
- **Lot ID**: Unique identifier for each production lot
- **Lot Quantity**: Number of units in the lot
- **Machine Number**: Identifier for the machine used
- **Defects**: Various types of defects including Contamination, Dent, Scratch, Discoloration, Delamination, Foreign Material, and Voids

## Key Performance Indicators (KPIs)
The following KPIs are derived from the data:
- **Yield per Month**: Productivity.
- **Defect Rate**: Percentage of defective items in each lot.
- **Total Defects per Lot**: Total number of defects in each lot.
- **Defects per Defect Type**: Average number of each defect type across all lots.
- **Defect Rate by Machine**: Average defect rate for each machine.
- **Operator Performance**: Defect rate associated with each operator.
- **Production Output**: Total quantity produced by each machine and operator.

Calculations in DAX:
**Defect Rate:**
DAX
Copy code
Defect Rate = DIVIDE([Total Defects], [Lot Quantity]) * 100

**Total Defects per Lot:**
This calculation depends on how your data is structured in Power BI. Assuming you have a table named 'Defects' with columns for each type of defect, you can sum them up using the SUMX function:
DAX
Copy code
Total Defects per Lot = SUMX(Defects, Defects[Contamination] + Defects[Dent] + Defects[Scratch] + Defects[Discoloration] + Defects[Delamination] + Defects[Foreign Material] + Defects[Voids])

**Average Defects per Type:**
DAX
Copy code
Average Defects per Type = AVERAGE(Defects[Specific Defect Type])

**Defect Rate by Machine:**
DAX
Copy code
Defect Rate by Machine = DIVIDE(SUM(Defects[Total Defects per Lot]), SUM(Defects[Lot Quantity for Machine])) * 100

**Operator Performance:**
DAX
Copy code
Defect Rate by Operator = DIVIDE(SUM(Defects[Total Defects per Lot]), SUM(Defects[Lot Quantity for Operator])) * 100

**Production Output:**
DAX
Copy code
Total Output by Machine = SUM(Defects[Lot Quantity for Machine])
Total Output by Operator = SUM(Defects[Lot Quantity for Operator])

## Usage
To use this analysis:
1. **Data Preparation**: Ensure your dataset is correctly formatted with the required fields.
2. **Calculation**: Use the provided formulas to calculate the KPIs.
3. **Analysis**: Evaluate the KPIs to identify areas for improvement in production quality and efficiency.

## Example
Here is an example of calculating KPIs for a sample lot:
- **Lot ID**: DF539
- **Lot Quantity**: 9329
- **Defects**: Contamination: 25, Dent: 69, Scratch: 34, Discoloration: 69, Delamination: 76, Foreign Material: 97, Voids: 28

**Total Defects per Lot**:
\[ 25 + 69 + 34 + 69 + 76 + 97 + 28 = 398 \]

**Defect Rate**:
\[ \frac{398}{9329} \times 100 \approx 4.27\% \]



**## Project Setup**
To set up this project:
1. Clone the repository.
   ```bash
   git clone <repository-url>


**Contributing**
Contributions are welcome! Please submit a pull request or open an issue to discuss what you would like to change.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.


**Contact**
For any questions or suggestions, please contact [Your Name] at [Your Email].