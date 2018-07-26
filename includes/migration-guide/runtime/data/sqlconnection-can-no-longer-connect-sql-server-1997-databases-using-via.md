### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection artık SQL Server 1997'den veya VIA bağdaştırıcısı kullanarak veritabanlarına bağlanabilir

|   |   |
|---|---|
|Ayrıntılar|Kullanarak SQL Server veritabanlarına bağlantı [sanal arabirim bağdaştırıcısı (VIA) protokolünü](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) artık desteklenmemektedir. Bir SQL Server veritabanına bağlanmak için kullanılan protokol, bağlantı dizesinde görülebilir. VIA bağlantı aracılığıyla içerecek:&lt;servername&gt;. VIA dışındaki bir protokolü aracılığıyla bu uygulamaya SQL'e bağlanma, (tcp: veya np: gibi), sonra hiçbir değişiklik karşılaşıldı. Ayrıca, SQL Server 7 (1997'den) bağlantı artık desteklenmemektedir.|
|Öneri|VIA Protokolü kullanım dışı olduğundan SQL veritabanlarına bağlanmak için alternatif bir protokolü kullanılmalıdır. En yaygın kullanılan protokol, TCP/IP'yi ' dir. TCP/IP protokolünün etkinleştirilmesi için yönergeler bulunabilir [burada](https://msdn.microsoft.com/library/bb909712.aspx). Veritabanı yalnızca gelen içinde intranet erişilirse, paylaşılan kanallar Protokolü'nü Ağ yavaşsa daha iyi performans sağlayabilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

