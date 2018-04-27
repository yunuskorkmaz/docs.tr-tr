### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET şimdi bozuk SQL bağlantıları otomatik olarak yeniden dener

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.1 başlayarak, .NET Framework bozuk SQL bağlantıları otomatik olarak yeniden deneyecek. Bu genellikle uygulamaları daha güvenilir, bir uygulama, bilmesi gerekir kenar durumlar vardır yapar ancak bazı eylemleri yeniden bağlanma sırasında yararlanabilmeniz bağlantı kesildi.|
|Öneri|Bu özellik istenmeyen uyumluluk sorunları nedeniyle ise, bu ayarı devre dışı bırakılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> özelliği, bir bağlantı dizesi (veya <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) 0.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|

