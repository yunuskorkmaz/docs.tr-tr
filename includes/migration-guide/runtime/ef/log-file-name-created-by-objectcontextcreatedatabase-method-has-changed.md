### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>SQL Server belirtimleri eşleşecek şekilde değiştirdi. ObjectContext.CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı

|   |   |
|---|---|
|Ayrıntılar|Zaman <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> yöntemi çağrıldığında ya da doğrudan ya da Code First SqlClient sağlayıcısı ve bağlantı dizesindeki AttachDBFilename değeri kullanılarak, (burada filename adıdır filename.ldf yerine filename_log.ldf adlı bir günlük dosyası oluşturur AttachDBFilename değeri tarafından belirtilen dosya). Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.|
|Öneri|Günlük dosyası adı bir uygulama için önemliyse, uygulama standart _log.ldf dosya adı biçimi beklenir güncelleştirilmesi gerekir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

