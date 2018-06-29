### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Çözümler bir SQL Server veritabanına TCP/IP bağlantı kurmaya çalışan `localhost` başarısız

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1, çözümler bir SQL Server veritabanına TCP/IP bağlantı kurmaya çalışan <code>localhost</code> hatasıyla başarısız oluyor &quot;SQL Server bağlantı kurulmaya çalışılırken ağ ile ilişkili veya örneğe özgü bir hata oluştu. Sunucu bulunamadı veya erişilebilir değildi. Örnek adının doğru olduğundan ve SQL Server Uzak bağlantılara izin verecek şekilde yapılandırıldığından emin olun. (sağlayıcısı: SQL ağ arabirimleri, hata: 26 - Server/örnek belirtilen hata bulma)&quot;|
|Öneri|Bu sorunu ele ve .NET Framework 4.6.2 önceki davranış geri. Çözümler bir SQL Server Database bağlanmak için <code>localhost</code>, .NET Framework 4.6.2'ye yükseltin.|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|çalışma zamanı|

