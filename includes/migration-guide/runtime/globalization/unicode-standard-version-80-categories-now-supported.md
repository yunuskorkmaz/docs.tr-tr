### <a name="unicode-standard-version-80-categories-now-supported"></a>Şimdi desteklenen Unicode standart sürümü 8.0 kategorileri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, Unicode verileri Framework'te sürüm 8.0 standart sürümünü 6.3 Unicode'dan yükseltildi.  .NET Framework 4.6.2 Unicode karakter kategorisinde isterken bazı sonuçları önceki .NET Framework sürüm sonuçlarında eşleşmeyebilir.  Bu çoğunlukla Cherokee heceleri etkiler ve Yeni Day lu sesli harf işaretleri ve ses işaretleri değiştirin.|
|Öneri|Kod gözden geçirin ve sabit kodlanmış Unicode karakter kategorilerindeki bağlıdır mantığı Kaldır/Değiştir.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

