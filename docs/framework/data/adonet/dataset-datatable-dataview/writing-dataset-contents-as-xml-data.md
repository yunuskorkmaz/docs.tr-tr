---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: c8a5c747e4ec60fcb97edf631aa3a0ae184ffec5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173724"
---
# <a name="writing-dataset-contents-as-xml-data"></a>XML Verileri Olarak DataSet İçeriği Yazma

ADO.NET içinde <xref:System.Data.DataSet> , şemasına sahip veya olmadan BIR XML temsili yazabilirsiniz. Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır. Şema, <xref:System.Data.DataSet> ilişki ve kısıtlama tanımlarının tablo tanımlarını içerir.  
  
 Bir, <xref:System.Data.DataSet> XML verileri olarak yazıldığında, içindeki satırlar <xref:System.Data.DataSet> geçerli sürümlerinde yazılır. Ancak, <xref:System.Data.DataSet> hem geçerli hem de satırların orijinal değerlerinin dahil edilmesini sağlamak için de bir DiffGram olarak yazılabilir.  
  
 Öğesinin XML temsili <xref:System.Data.DataSet> bir dosyaya, akışa, bir **XmlWriter**'a veya bir dizeye yazılabilir. Bu seçimler, öğesinin XML gösterimini taşımanın harika bir esnekliğini sağlar <xref:System.Data.DataSet> . Öğesinin XML temsilini <xref:System.Data.DataSet> bir dize olarak almak için aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** şema BILGILERININ olmayan XML gösterimini döndürür <xref:System.Data.DataSet> . Şema bilgilerini <xref:System.Data.DataSet> (XML şeması olarak) bir dizeye yazmak Için **GetXmlSchema**kullanın.  
  
 Bir <xref:System.Data.DataSet> dosyaya, akışa veya **XmlWriter**'A yazmak için **WriteXml** yöntemini kullanın. **WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir. Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin. XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.  
  
 Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.  
  
|XmlWriteMode seçeneği|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|XML <xref:System.Data.DataSet> şeması olmadan, XML verilerinin geçerli içeriğini yazar. Bu varsayılan seçenektir.|  
|**WriteSchema seçeneğine ayarlayın**|<xref:System.Data.DataSet>XML verilerinin güncel içeriğini ilişkisel yapıda satır ıçı XML şeması olarak yazar.|  
|**Içeriyor**|<xref:System.Data.DataSet>Özgün ve geçerli değerler dahil olmak üzere bir DiffGram olarak tümünü yazar. Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).|  
  
 DataRelation nesneleri içeren bir XML temsili yazarken <xref:System.Data.DataSet> , sonuçta **DataRelation** elde edilen XML 'nin ilgili üst öğeleri içinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz. Bunu gerçekleştirmek için, **DataRelation** 'ı öğesine eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın <xref:System.Data.DataSet> . Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).  
  
 Aşağıda bir dosyasına bir dosyasının XML gösteriminin nasıl yazılacağı hakkında iki örnek verilmiştir <xref:System.Data.DataSet> . İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir. İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Sütunları XML öğeleri, öznitelikleri ve metin ile eşleme  

 **DataColumn** nesnesinin **ColumnMapping** özelliğini kullanarak bir tablo sütununun XML olarak nasıl temsil edileceğini belirtebilirsiniz. Aşağıdaki tablo, bir tablo sütununun **ColumnMapping** özelliği ve elde edilen XML Için farklı **MappingType** değerlerini gösterir.  
  
|MappingType değeri|Açıklama|  
|-----------------------|-----------------|  
|**Dosyalarında**|Bu varsayılan seçenektir. Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır. Örneğin:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Öznitelik**|Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır. Örneğin:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**'Dir**|Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır. Örneğin:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> **Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.|  
|**Lene**|Sütun XML çıktısında yazılmadı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)
- [XSD Olarak DataSet Schema Bilgilerini Yazma](writing-dataset-schema-information-as-xsd.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
