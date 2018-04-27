### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection artık SQL Server 1997 veya VIA bağdaştırıcısı kullanarak veritabanlarına bağlanabilir

|   |   |
|---|---|
|Ayrıntılar|Bağlantıları kullanarak SQL Server veritabanlarına [sanal arabirimi bağdaştırıcı (VIA) Protokolü](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) artık desteklenmemektedir. Bir SQL Server veritabanına bağlanmak için kullanılan protokol bağlantı dizesinde görünür olur. VIA bağlantısı aracılığıyla içerir:&lt;servername&gt;. Bu uygulama için SQL VIA dışında bir protokolü aracılığıyla bağlanıyor varsa (tcp: veya np: örneğin), en son değişiklik karşılaştı sonra. Ayrıca, SQL Server 7 (1997) bağlantıları artık desteklenmemektedir.|
|Öneri|VIA Protokolü kullanım dışı SQL veritabanlarına bağlanmak için bir alternatif Protokolü kullanılmalıdır. Kullanılan en yaygın TCP/IP'yi kuralıdır. TCP/IP protokolünün etkinleştirilmesi için yönergeler bulunabilir [burada](https://msdn.microsoft.com/library/bb909712.aspx). Veritabanı yalnızca intranet içinde erişilen, paylaşılan kanallar protokolü ağ yavaşsa daha iyi performans sağlayabilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

