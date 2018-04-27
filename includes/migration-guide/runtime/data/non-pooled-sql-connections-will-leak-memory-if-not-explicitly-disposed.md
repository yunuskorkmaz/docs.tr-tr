### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>SQL bağlantıları olmayan havuza bellek sızıntısı değilse açıkça atıldı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 havuza olmayan (Dispose, kapatma, veya kullanarak) açıkça sunulmaz SQL bağlantıları bellek sızıntısı|
|Öneri|Bu sorun bir .NET Framework 4.5 hizmet verme güncelleştirme düzeltilmiştir. Lütfen bu sorunu gidermek için .NET Framework 4.5, veya .NET Framework 4.5.1 yükseltin ya da üstü güncelleştirin. Alternatif olarak, bu sorunu kullanarak kalmayabilir <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> içinde bir &#39;kullanarak&#39; (en iyi uygulama olmayan) desen veya açıkça çağırarak Dispose ya da bağlantı artık gerekli olmadığında kapatın.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

