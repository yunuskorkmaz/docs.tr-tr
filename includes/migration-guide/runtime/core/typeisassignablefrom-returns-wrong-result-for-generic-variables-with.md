### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom kısıtlamalarına sahip genel değişkenler için yanlış sonucunu döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde <xref:System.Type.IsAssignableFrom(System.Type)> yanlış döndürür <code>false</code> bazı kısıtlamalar ile genel türleri için tüm durumlarda.|
|Öneri|Hizmet bir güncelleştirmede bu sorun giderilmiştir. Lütfen bu sorunu gidermek için .NET Framework 4.5, veya .NET Framework 4.5.1 yükseltin ya da üstü güncelleştirin. Alternatif olarak, genel parametrelerindeki kısıtlamalar genel türleri ile IsAssignableFrom kullanmaktan kaçının. Yansıma API'leri, bir iş-geçici kullanılabilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|Çözümleyiciler|<ul><li>CD0089</li></ul>|

