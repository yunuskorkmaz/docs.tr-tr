### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>SQL Server spesifikasyonlarına eşleştirilecek ObjectContext.CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Zaman <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> yöntemi çağrıldığında ya da doğrudan ya da Code First SqlClient sağlayıcısı ve bağlantı dizesinde AttachDBFilename değeri ile kullanarak (dosya adı olduğu adını filename_log.ldf filename.ldf yerine adlandırılmış bir günlük dosyası oluşturur AttachDBFilename değeri tarafından belirtilen dosya). Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.|
|Öneri|Günlük dosyası adı bir uygulama için önemli ise, uygulama standart _log.ldf dosya adı biçimi beklenir güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|

