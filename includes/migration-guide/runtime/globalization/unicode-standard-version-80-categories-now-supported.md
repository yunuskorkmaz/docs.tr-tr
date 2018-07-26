### <a name="unicode-standard-version-80-categories-now-supported"></a>Artık desteklenen Unicode standart sürümü 8.0 kategorileri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, Unicode verilerini sürüm 8.0 sürümü 6.3 Unicode standart katmandan yükseltildi.  .NET Framework 4.6.2 Unicode karakter kategorileri isterken, bazı sonuçları önceki .NET Framework sürümlerini sonuçları eşleşmeyebilir.  Bu çoğunlukla Çeroki hece etkiler ve Yeni Day lu sesli harfler işaretleri ve ses işaretleri değiştirin.|
|Öneri|Kodu gözden geçirin ve Unicode karakter kategorileri sabit kodlanmış bağlıdır mantıksal Kaldır/Değiştir.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

