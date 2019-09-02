---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: b8a8656bb68832a09490e656903fd68788bdeb1d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203103"
---
# <a name="writing-dataset-contents-as-xml-data"></a>XML Verileri Olarak DataSet İçeriği Yazma
ADO.NET içinde, şemasına sahip veya olmadan bir <xref:System.Data.DataSet>XML temsili yazabilirsiniz. Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır. Şema, ilişki ve kısıtlama tanımlarının tablo tanımlarını <xref:System.Data.DataSet> içerir.  
  
 Bir <xref:System.Data.DataSet> , XML verileri olarak yazıldığında, <xref:System.Data.DataSet> içindeki satırlar geçerli sürümlerinde yazılır. Ancak, hem <xref:System.Data.DataSet> geçerli hem de satırların orijinal değerlerinin dahil edilmesini sağlamak için de bir DiffGram olarak yazılabilir.  
  
 Öğesinin <xref:System.Data.DataSet> XML temsili bir dosyaya, akışa, bir **XmlWriter**'a veya bir dizeye yazılabilir. Bu seçimler, <xref:System.Data.DataSet>öğesinin XML gösterimini taşımanın harika bir esnekliğini sağlar. Öğesinin <xref:System.Data.DataSet> XML temsilini bir dize olarak almak için aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** şema bilgilerinin <xref:System.Data.DataSet> olmayan XML gösterimini döndürür. Şema bilgilerini <xref:System.Data.DataSet> (XML şeması olarak) bir dizeye yazmak için **GetXmlSchema**kullanın.  
  
 Bir <xref:System.Data.DataSet> dosyaya, akışa veya **XmlWriter**'a yazmak için **WriteXml** yöntemini kullanın. **WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir. Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin. XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.  
  
 Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.  
  
|XmlWriteMode option|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|XML şeması olmadan, XML verilerinin <xref:System.Data.DataSet> geçerli içeriğini yazar. Bu varsayılandır.|  
|**WriteSchema seçeneğine ayarlayın**|XML verilerinin güncel içeriğini <xref:System.Data.DataSet> ilişkisel yapıda satır içi xml şeması olarak yazar.|  
|**Içeriyor**|Özgün ve geçerli <xref:System.Data.DataSet> değerler dahil olmak üzere bir DiffGram olarak tümünü yazar. Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).|  
  
 <xref:System.Data.DataSet> **DataRelation** nesneleri içeren bir XML temsili yazarken, sonuçta elde edilen XML 'nin ilgili üst öğeleri içinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz. Bunu gerçekleştirmek için, **DataRelation** 'ı öğesine <xref:System.Data.DataSet>eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın. Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).  
  
 Aşağıda bir dosyasına bir <xref:System.Data.DataSet> dosyasının XML gösteriminin nasıl yazılacağı hakkında iki örnek verilmiştir. İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir. İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.  
  
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
|**Öğe**|Bu varsayılandır. Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır. Örneğin:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Öznitelik**|Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır. Örneğin:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**'Dir**|Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır. Örneğin:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> **Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.|  
|**Lene**|Sütun XML çıktısında yazılmadı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)
- [XSD Olarak DataSet Schema Bilgilerini Yazma](writing-dataset-schema-information-as-xsd.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
