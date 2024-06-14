# ASP.NET

https://github.com/gtechsltn/all

https://github.com/gtechsltn/asp-net

https://github.com/gtechsltn/asp-net-core

# Paging

## SQL

https://stackoverflow.com/questions/9848592/dapper-paging

https://andypalmer.dev/posts/pagination-with-dapper/

```
SELECT  *
FROM    ( SELECT    ROW_NUMBER() OVER ( ORDER BY InsertDate) AS RowNum, *
          FROM      Posts
          WHERE     InsertDate >= '1900-01-01'
        ) AS result
WHERE   RowNum >= 1
    AND RowNum < 20
ORDER BY RowNum
```

## SQL Server

https://www.carlrippon.com/scalable-and-performant-asp-net-core-web-apis-sql-server-isolation-level/

https://www.sqlshack.com/pagination-in-sql-server/

```
SELECT FruitName, Price
FROM SampleFruits
ORDER BY Price
OFFSET 5 ROWS FETCH NEXT 6 ROWS ONLY
```

```
DECLARE @PageNumber AS INT
DECLARE @RowsOfPage AS INT
SET @PageNumber=2
SET @RowsOfPage=4
SELECT FruitName,Price FROM SampleFruits
ORDER BY Price 
OFFSET (@PageNumber-1)*@RowsOfPage ROWS
FETCH NEXT @RowsOfPage ROWS ONLY
```

```
DECLARE @PageNumber AS INT
DECLARE @RowsOfPage AS INT
DECLARE @SortingCol AS VARCHAR(100) ='FruitName'
DECLARE @SortType AS VARCHAR(100) = 'DESC'
SET @PageNumber=1
SET @RowsOfPage=4
SELECT FruitName,Price FROM SampleFruits
ORDER BY 
CASE WHEN @SortingCol = 'Price' AND @SortType ='ASC' THEN Price END ,
CASE WHEN @SortingCol = 'Price' AND @SortType ='DESC' THEN Price END DESC,
CASE WHEN @SortingCol = 'FruitName' AND @SortType ='ASC' THEN FruitName END ,
CASE WHEN @SortingCol = 'FruitName' AND @SortType ='DESC' THEN FruitName END DESC
OFFSET (@PageNumber-1)*@RowsOfPage ROWS
FETCH NEXT @RowsOfPage ROWS ONLY
```

```
DECLARE @PageNumber AS INT
DECLARE @RowsOfPage AS INT
DECLARE @MaxTablePage AS FLOAT 
SET @PageNumber=1
SET @RowsOfPage=4
SELECT @MaxTablePage = COUNT(*) FROM SampleFruits
SET @MaxTablePage = CEILING(@MaxTablePage/@RowsOfPage)
WHILE @MaxTablePage >= @PageNumber
BEGIN
  SELECT FruitName, Price FROM SampleFruits
  ORDER BY Price 
  OFFSET (@PageNumber - 1) * @RowsOfPage ROWS
  FETCH NEXT @RowsOfPage ROWS ONLY
  SET @PageNumber = @PageNumber + 1
END
```

## WinForms

https://github.com/jinweijie/Dapper.PagingSample/

https://www.codeproject.com/Articles/1257860/Paging-WPF-DataGrid

https://www.codeproject.com/Articles/1198544/Pagination-in-asp-net-mvc-core-entity-framework-an

## C# SQL Database pagination sample using Dapper ORM.

https://gist.github.com/palmerandy/f41f85b91274feb88be627e1c30d7347

https://gist.github.com/gtechsltn/686af7fca13601db9d20f6cd8789c8f0

## C# SQL Database pagination using Dapper ORM

https://andypalmer.dev/posts/pagination-with-dapper/


## Pagination in a .NET Web API with EF Core

https://henriquesd.medium.com/pagination-in-a-net-web-api-with-ef-core-2e6cb032afb7

https://github.com/henriquesd/PaginationDemo/

# Resources

https://github.com/dpaquette/BugTracker.NET (JavaScrip + ASP.NET MVC)

https://github.com/dpaquette/SocialRecipes

https://github.com/dpaquette/EntityFramework.Seeder

https://github.com/dpaquette/SeedingDatabaseFromCSV

