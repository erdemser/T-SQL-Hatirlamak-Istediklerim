# T-SQL Mükerrer Kayıtları Listeleme

`Select KOLONADI, Count(KOLONADI) From TABLOADI Group By KOLONADI Having Count (KOLONADI) > 1`


# T-SQL Fetch Döngüsü

    --Değişken tanımı
    DECLARE @PeopleId uniqueidentifier
    
    --Döngü yapılacak tablo
    DECLARE DONGU CURSOR FOR
    	SELECT Id FROM People
      
    OPEN DONGU
    FETCH NEXT FROM DONGU INTO @PeopleId
    
    WHILE @@FETCH_STATUS = 0
    	BEGIN
    	PRINT @PeopleId
    	FETCH NEXT FROM DONGU INTO @PeopleId
    	END
      
    CLOSE DONGU
    DEALLOCATE DONGU
    
#### Döngü Yerine Kullanılabilir

    DECLARE  @sql NVARCHAR(MAX) = ''
	SELECT @sql += 'EXEC StoredProcedure ''' + CONVERT(VARCHAR(50), Id) + ''',''' 
        + CONVERT(VARCHAR(50),MemberId) + ''';' 
    FROM People
	--PRINT @sql
	EXEC sp_executesql @sql
