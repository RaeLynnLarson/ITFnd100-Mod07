
# Title
  **Dev:** *RLarson*  
  **Date:** *2.27.2024*
## Introduction
  Functions are used for transforming and manipulating the data within a database. They come in a wide variety and are very versatile, allowing the user to get a variety of answers from their data. 
## Scalar functions
Scalar functions only return a single value. They include the answer of calculations, and well as the answers to true-or-false queries. Scalar functions can be very useful in adding constraints or columns to tables where otherwise the needed data would not exist in the correct form.
```
Create Function dbo.MultiplyValues(@Value1 Float, @Value2 Float)
 Returns Float 
 As
  Begin
   Return(Select @Value1 * @Value2);
  End 
go
-- Calling the function
Select Tempdb.dbo.MultiplyValues(4, 5);
go
```
* From Module 07 notes from IT FND 130. *
## Tabular functions
Tabular functions, in contrast, return a table as an answer to a query. This can be useful when trying to sort a table by a certain parameter. These UDF’s are a bit like views but include a variable that the table will be selected by. They come in two types: in-line and multi-statement. 
### -	In-line:  An In-line UDF returns one table per specified variable, no additional processing needed.  An example is shown below.
```
Create Function dbo.fFilmsByDuration (@Duration int)
  returns table
 as
  return (Select
  [Column 1],
  [Column 2],
  [Column n]
  from dbo.Northwind
go
```
### - -	Multi-statement function: The biggest difference between these and the Inline functions is that these have multiple statements in the one UDF. 
```
CREATE OR ALTER FUNCTION dbo.GetQuestionWithAnswers
(@PostId int)
RETURNS 
@results TABLE 
(PostId bigint,
Body nvarchar(max),
CreationDate datetime)
AS
BEGIN
--- Statement 1
--- statement 2
--- Statement n
Return
end
```
## Functions and Views 
###- Views are considered easier to use than functions and so are preferred when making a table. To make a unique column, a user can use scalar UDF’s in their view creation so that the data they want is there. Tabular functions are very useful when a user wants to make several different views without having to change one clause. A function will allow them to only have to code everything once.

