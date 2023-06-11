# excel-data-cleanup-project
A repository showcasing before-and-after data cleaning and transformation project in Excel demonstrating effective techniques for improving data quality and usability.
We use a raw dataset of EA Sports' latest installment of their hit FIFA series - FIFA21 from kaggle which can be found [here.](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring?select=fifa21+raw+data+v2.csv)



**Step 1**

To facilitate numeric calculations, the string data type in the 'height' and 'weight' columns, which have units postfixed to each record, needs to be converted to an integer type.

- Firstly, create new columns, 'Height (cm)' and 'Weight (kg)', and remove the postfix using the formula `=LEFT(N2, LEN(N2)-2)`.

- This formula extracts the numerical portion by removing the last two letters ('kg' and 'cm') from each respective column.
- Drag down the formulas in the ''Height (cm)' and 'Weight (kg)' columns to apply them to the rest of the cells.

- Lastly, we can change the data type to number using the 'Format Cells' options.


**Step 2**

On the column `Joined`, we have a full date in the format `MM-DD-YYYY`. In order to perfrom granular calculations, its a good idea to split the 'Joined' column into separate columns for year, month, and day in Excel. To do so, we follow these steps:

- Create a new column for the year:
In the first cell of the new column, add the title 'Year'.
Enter the formula `=YEAR(X2)` in the cell below the title.
This formula extracts the year from the date in cell X2.

- Create another new column for the month:
In the first cell of the new column, add the title 'Month'.
Enter the formula `=TEXT(X2, "mmm")` in the cell below the title.
This formula converts the date in cell X2 to a three-letter abbreviation of the month.

- Create a column for the day:
In the first cell of the new column, add the title 'Day'.
Enter the formula `=DAY(X2)` in the cell below the title.
This formula extracts the day from the date in cell X2.

- Drag these formulas down:
Drag the formulas in the 'Year', 'Month', and 'Day' columns down to apply them to the rest of the cells.
This will populate the columns with the respective year, month, and day values based on the 'Joined' column values in column X.

Following these steps will result in separate columns for the year, month, and day, derived from the 'Joined' column in Excel.


**Step 3**

If we look at the columns: value, wage, and release, we have `"M"` as the postfix and `‚Ç¨`. To clean and transform the value, wage, and release clause columns into columns of integers, we follow these:

- For Value:
    - Remove the '‚Ç¨' symbol and 'M' from the values:
    - Use the formula: `=(SUBSTITUTE(SUBSTITUTE(AA2, "‚Ç¨", ""), "M", ""))`
    - Multiply the result by 1,000,000 to convert it to an integer:
    - Use the final formula: `=(SUBSTITUTE(SUBSTITUTE(AA2, "‚Ç¨", ""), "M", "")) * 1000000`

- For Wage:
    - Remove the `'‚Ç¨'` symbol and `'K'` from the values:
    - Use the formula: `=(SUBSTITUTE(SUBSTITUTE(AC2, "‚Ç¨", ""), "K", ""))`
    - Multiply the result by 1,000 to convert it to an integer:
    - Use the final formula: `=(SUBSTITUTE(SUBSTITUTE(AC2, "‚Ç¨", ""), "K", "")) * 1000`

- For Release Clause:
    - Remove the `'‚Ç¨'` symbol and `'M'` from the values:
    - Use the formula: `=(SUBSTITUTE(SUBSTITUTE(AE2, "‚Ç¨", ""), "M", ""))`
    - Multiply the result by 1,000,000 to convert it to an integer:
    - Use the final formula: `=(SUBSTITUTE(SUBSTITUTE(AE2, "‚Ç¨", ""), "M", ""))* 1000000`

By following these steps and applying the respective formulas to the corresponding columns, the value, wage, and release clause columns will be transformed into columns of integers.

**Step 4**

To change the 'Hits' column to numerical form, we follow these steps:

- Create a new column named 'Hits(Updated)' right next to the column'Hits'.

- Apply the following formula to the first cell of the 'Hits(Updated)' column.

- Formula: `=IF(RIGHT(CI2,1)="K", LEFT(CI2,LEN(CI2)-1)*1000, CI2)`

This formula performs the following actions:

- Checks if the last character of the cell value in column CI is "K".
If it is "K", it removes the "K" character from the cell value and multiplies the remaining value by 1000.
If it is not "K", it leaves the cell value as is.

- By applying this formula to the 'Hits(Updated)' column and dragging it down to apply it to the rest of the cells, the column will be converted to numerical form, multiplying the values ending with "K" by 1000.

**Step 5**

In the contract column, we see that the range is separated by `~`. Let's change this to a more meaningful symbol: `-`.

- Create and apply the following formula to the Contract(Updated) column 
Formula: `=SUBSTITUTE(L2, "~", "-")`

- This formula performs the following action:
It searches for the tilde symbol (~) in the cell value of column L and replaces it with a hyphen (-).

- By applying this formula to the desired column and dragging it down to apply it to the rest of the cells, the tilde symbols will be substituted with hyphens, effectively performing the string substitution.
