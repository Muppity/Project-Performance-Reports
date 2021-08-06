# Sequence Use Case

## Requirements


| Item | Function Name   | Description | Complexity | Constraints |
| ---- |:------------:|:----------:|--------------------------------------  | ---------- |
| 1    |`Request Range`    | **This function will detail create a new range and return the start, end range and current index**   | ***8*** |  |
|1.0|Create Tables and objects |For Ranges and Unsed Ranges |3| These are going to be desgined only, due Dev team will deploy them directly into QA and Prod.
| 1.1 | Check Sequence in DB  | Check if the  Date and Type exists in the database | 3 | **(1)** Verify in **Ranges** and **Unused_Ranges** Tables with ***Date_UTC*** and ***Type*** if sequence already exists  **(2)** verify if the range fits if its a valid size (if fits take from there and decrease(-- ) and change the value) if not fits then increase the number ++ , **(3)** verify if the ***Date_UTC is Null*** then set SQL default, (Set default value in table)   |
| 1.2 | Create **range** and **unsued_rage** row  | insert into both tables the required row and calculate the  | 5| **(1)** Begin tran end tran, under try catch statements **(2)** use hint to **updlock**, verify the parameters if date is **NULL** then place the ANSI SQL minimum **(3)** insert rows in **Range** and **Unsed_Range** **(4)** unlock table and return the **Start_Range**, **Current_Range**, **Current_Index** |
| 2    | `Unset Put` | **This function will create a new sequence by returning back the series of the actual left index DCN** | ***8*** |
|2.1|Check Ranges and Unsed tables|Verify if ranges exists in **unused_range** and insert row or update  |3| **(1)** Verify if ranges exists, if yes then verify the new value for ranges based on the current_index in ranges table value.**(2)** updatelock update /insert  **(3)** return values. 


Format 
date       - AAAAMMDD - Date_UTC
String     - uniqueIdentifier           - Type     

