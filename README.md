# Advanced TRIM SQL SERVER

```sql
CREATE FUNCTION dbo.TRIM(@String VARCHAR(MAX))
  RETURNS VARCHAR(MAX)
BEGIN
    RETURN (CASE
        WHEN @String is NULL 
		    THEN NULL
        ELSE
            LTRIM(RTRIM(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(REPLACE(@String, CHAR(160), '[}'), CHAR(10), '[}'), CHAR(13), '[}'), char(9), '[}'), CHAR(32), '[}'), '}[', ''), '[}', CHAR(32))))
    END);
END
GO

```

```sql
-- Example of use:
select dbo.TRIM('  THIS IS A			 TEST STRING      ') as Example
```
