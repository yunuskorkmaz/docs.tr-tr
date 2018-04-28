### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException şimdi satır konumlarını düzgün ayarlar

|   |   |
|---|---|
|Ayrıntılar|Varsa <xref:System.Xml.Linq.LoadOptions.SetLineInfo> yük yönteme geçirilen değer ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri artık satırı bilgileri içerir.|
|Öneri|Varsayar özel durum işleme kod <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> değişmeyecek SetLineInfo XML yüklenirken kullanıldığında, bu özellikleri artık düzgün ayarlanacak beri kümesi güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

