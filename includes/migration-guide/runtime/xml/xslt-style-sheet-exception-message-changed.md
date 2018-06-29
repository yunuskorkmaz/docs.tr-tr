### <a name="xslt-style-sheet-exception-message-changed"></a>XSLT stil sayfası özel durum iletisi değiştirildi

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 XSLT dosyası çok karmaşık olduğunda hata iletisi metindir &quot;stil sayfası çok karmaşıktır.&quot; Önceki sürümlerde, hata iletisi edildi &quot;XSLT derleme hatası.&quot; Hata iletisindeki metne bağlı olan uygulama kodu artık çalışmaz. Ancak, bu değişiklik, gerçek etkisi olması gerekir böylece özel durum türleri aynı kalır.|
|Öneri|Yeni ileti beklenir bu hata koşulu gelen özel durum iletisi bağlı olarak herhangi bir uygulama kod güncelleştirmek veya kod yalnızca özel durum türüne bağlıdır (bile daha iyi) güncelleştirmesi (<xref:System.Xml.Xsl.XsltException?displayProperty=name>), hangi değişmemiştir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

