### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>OData URL'lerinde Değiştir yöntemi varsayılan olarak devre dışıdır

|   |   |
|---|---|
|Ayrıntılar|OData URL'lerinde Değiştir yöntemi, .NET Framework 4. 5 ' başlayarak, varsayılan olarak devre dışıdır. OData Değiştir (varsayılan olarak şimdi) devre dışı bırakıldığında (nadir bir durumdur) Değiştir işlevlerini de dahil olmak üzere kullanıcı isteklerinin başarısız olur.|
|Öneri|Replace yöntemi gerekiyorsa (olduğu nadir bir durumdur), yapılandırma ayarları aracılığıyla yeniden etkin olabilir (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Ancak, bir etkin Değiştir yöntemi güvenlik açıkları açabilir ve yalnızca inceledikten sonra kullanılmalıdır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|

