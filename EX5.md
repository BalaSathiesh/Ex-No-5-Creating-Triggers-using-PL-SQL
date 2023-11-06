# Ex. No: 5 Creating Triggers using PL/SQL
## DATE:1/9/23
### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
![image](https://github.com/BalaSathiesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/128462891/e1dc1d54-ad33-4255-8594-aafea29e486d)

### Create salary_log table
![image](https://github.com/BalaSathiesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/128462891/4bf7377f-7c3f-446b-a36b-e41b23771046)

### PLSQL Trigger code
```
 create or replace trigger log_salary1_update
 before update on emp2
 for each row
 declare
 old_salary number;
 new_salary number;
 begin
 old_salary := :OLD.salary;
 new_salary := :NEW.salary;
 if old_salary <> new_salary then
 insert into logs_salary2(empid, empname, old_salary, new_salary, update_date)
 values(:OLD.empid, : OLD.empname, old_salary, new_salary, SYSDATE);
 end if;
 end;
 /
```
### Output:
![image](https://github.com/BalaSathiesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/128462891/8ef3a7d4-b4bc-4127-a349-f48c9f09a51f)

### Result:
Therefore,Creating Triggers using PL/SQL Exceuted Successfully.
