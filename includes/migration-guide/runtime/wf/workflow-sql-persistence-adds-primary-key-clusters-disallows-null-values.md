### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>İş akışı SQL Kalıcılık birincil anahtar kümeleri ve bazı sütunlarda null değerlere izin vermez ekler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ile başlayarak, SQL iş akışı örneği deposu (SWIS) için SqlWorkflowInstanceStoreSchema.sql komut dosyası tarafından oluşturulan tabloları kümelenmiş birincil tuşlarını kullanın. Bu nedenle, kimlikleri desteklemediği <code>null</code> değerleri. SWIS işlemi, bu değişiklikten etkilenmez. SQL Server işlem çoğaltma desteklemek için güncelleştirmeleri yapıldı.|
|Öneri|Bu değişiklik deneyimi için SQL dosyası SqlWorkflowInstanceStoreSchemaUpgrade.sql var olan yüklemelerin uygulanmış olması gerekir. Yeni veritabanı yüklemeleri otomatik olarak değiştir sahip olacaktır.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

