### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException artık satır konumlarını düzgün ayarlar

|   |   |
|---|---|
|Ayrıntılar|Varsa <xref:System.Xml.Linq.LoadOptions.SetLineInfo> yük yönteme geçirilen değer ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri satır bilgileri içerir.|
|Öneri|Varsayar özel durum işleme kodları <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> değişmeyecek SetLineInfo XML yüklenirken kullanıldığında bu özellikler artık düzgün şekilde ayarlanır bu yana kümesi güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|

