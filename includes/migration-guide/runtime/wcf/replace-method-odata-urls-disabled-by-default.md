### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL'lerinde Değiştir yöntemi varsayılan olarak devre dışıdır

|   |   |
|---|---|
|Ayrıntılar|OData URL'lerinde Değiştir yöntemi, .NET Framework 4. 5 ' başlayarak, varsayılan olarak devre dışıdır. OData Değiştir (şimdi varsayılan olarak) devre dışı bırakıldığında (Bu nadir) Değiştir işlevleri dahil olmak üzere herhangi bir kullanıcı isteğinin başarısız olur.|
|Öneri|Replace yöntemi gerekiyorsa (olduğu genel olmayan), yapılandırma ayarları aracılığıyla yeniden etkin olabilir (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Ancak, bir etkin Değiştir yöntemi güvenlik açıklarını açabilirsiniz ve yalnızca inceledikten sonra kullanılmalıdır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

