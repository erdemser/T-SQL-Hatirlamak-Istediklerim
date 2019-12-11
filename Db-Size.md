Database boyutunu öğrenme
---
    SELECT DB_NAME(database_id) AS DatabaseName,
           Name AS Logical_Name,
           Physical_Name,
           (size * 8) / 1024 SizeMB
    FROM sys.master_files
    WHERE DB_NAME(database_id) = 'DbAdı'
