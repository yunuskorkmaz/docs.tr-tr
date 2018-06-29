### <a name="xslt-forward-compat-now-works"></a>XSLT iletme compat şimdi çalışıyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4'te XSLT 1.0 ileriye dönük uyumluluğu aşağıdaki sorunlarla karşılaştı:<ul><li>Sürümü 2.0 değerine ayarlanmış bir stil sayfasının yüklenmesi başarısız oldu ve ayrıştırıcı tanınmayan bir XSLT 1.0 yapısıyla karşılaştı.</li><li><code>xsl:sort</code> Stil sayfası sürüm 1.1 için ayarlarsanız verileri sıralamak yapı başarısız oldu.</li></ul>.NET Framework 4.5, bu sorunları sabit ve XSLT 1.0 ileriye dönük uyumluluğu modu düzgün çalışır.|
|Öneri|Sort dikkate göre verileri farklı bazı durumlarda sıralanır ancak çoğu uygulamalar etkilenmez, olması gerekir. Varsa <code>xsl:sort</code> olan 1.1 stil sayfasında kullanıldığında, uygulamaları veri sıralanmamış siparişte bağlı değil olduğunu onaylayın. Uygulamaları davranışı sıralama 4.0 üzerinde kullanıyorsa, kaldırma <code>xsl:sort</code> stil sayfasından.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|

