### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument fazladan satırlık metin gösterebilir

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, bir <xref:System.Windows.Documents.FlowDocument> öğesi .NET Framework 4.5, .NET Framework 4. 0'çalıştırdığınızda görüntülenme için karşılaştırıldığında üzerinde çalışırken metnin fazladan bir satır görüntüler. Neden kötü veya okunaklı olmama görüntülenecek herhangi bir metin değişikliğinin bilinen hiçbir durumlar vardır, ancak, daha önce gelen atlandı görüntülenecek metni neden bir <xref:System.Windows.Documents.FlowDocument>kullanıcının görüntüleyin.|
|Öneri|Bazı durumlarda görüntü öğenin PageHeight özelliği tarafından azalan önceki görüntülenen satır sayısı geri yükleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

