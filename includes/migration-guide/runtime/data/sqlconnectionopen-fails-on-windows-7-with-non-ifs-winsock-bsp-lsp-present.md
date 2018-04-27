### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open IFS Winsock BSP veya LSP mevcut Windows 7'de başarısız olur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Data.SqlClient.SqlConnection.Open> ve <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> IFS Winsock BSP veya LSP sahip bir Windows 7 makine üzerinde çalışan bilgisayarda .NET Framework 4. 5 ' başarısız. IFS BSP veya LSP yüklü olup olmadığını belirlemek için <code>netsh WinSock Show Catalog</code> komut ve inceleyin her <code>Winsock Catalog Provider Entry</code> döndürülen öğe. Hizmet bayrakları değere sahip olursa <code>0x20000</code> bit kümesi, sağlayıcı IFS tanıtıcıları kullanır ve düzgün çalışır. Varsa <code>0x20000</code> bit Temizle (ayarlanmamış), IFS BSP veya LSP.|
|Öneri|.NET Framework yükselterek önlenebilir için .NET Framework 4.5.2, bu hatanın düzeltildiğini. Alternatif olarak, tüm yüklü olmayan - IFS Winsock LSPs kaldırarak önlenebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

