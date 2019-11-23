---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833964"
---
# <a name="writing-dataset-contents-as-xml-data"></a>XML Verileri Olarak DataSet İçeriği Yazma
ADO.NET ' de, şemasına sahip veya olmayan bir <xref:System.Data.DataSet>XML temsili yazabilirsiniz. Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır. Şema, ilişki ve kısıtlama tanımlarının yanı sıra <xref:System.Data.DataSet> tablo tanımlarını içerir.  
  
 Bir <xref:System.Data.DataSet> XML verisi olarak yazıldığında, <xref:System.Data.DataSet> satırları geçerli sürümlerinde yazılır. Ancak, <xref:System.Data.DataSet> hem geçerli hem de satırların orijinal değerlerinin dahil edilmesini sağlamak için de bir DiffGram olarak yazılabilir.  
  
 <xref:System.Data.DataSet> XML temsili bir dosyaya, akışa, bir **XmlWriter**'a veya dizeye yazılabilir. Bu seçenekler, <xref:System.Data.DataSet>XML gösterimini taşımanın harika bir esnekliğini sağlar. <xref:System.Data.DataSet> XML gösterimini bir dize olarak almak için aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** , şema bilgisi olmadan <xref:System.Data.DataSet> XML gösterimini döndürür. Şema bilgilerini bir dizeye <xref:System.Data.DataSet> (XML şeması olarak) yazmak için **GetXmlSchema**kullanın.  
  
 Bir dosyaya, akışa veya **XmlWriter**'a <xref:System.Data.DataSet> yazmak için **WriteXml** yöntemini kullanın. **WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir. Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin. XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.  
  
 Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.  
  
|XmlWriteMode option|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|XML şeması olmadan <xref:System.Data.DataSet> geçerli içeriğini XML verisi olarak yazar. Bu varsayılandır.|  
|**WriteSchema seçeneğine ayarlayın**|<xref:System.Data.DataSet> geçerli içeriğini, ilişkisel yapıda satır içi XML şeması olarak XML verileri olarak yazar.|  
|**Içeriyor**|Özgün ve geçerli değerler dahil olmak üzere tüm <xref:System.Data.DataSet> DiffGram olarak yazar. Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).|  
  
 **DataRelation** nesneleri içeren BIR <xref:System.Data.DataSet> XML temsili yazarken, sonuçta elde edilen XML 'nin ilgili üst öğelerinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz. Bunu gerçekleştirmek **için, <xref:System.Data.DataSet>** **DataRelation** ' ın **Nested** özelliğini **true** olarak ayarlayın. Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).  
  
 Aşağıda bir <xref:System.Data.DataSet> XML gösteriminin bir dosyaya nasıl yazılacağı hakkında iki örnek verilmiştir. İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir. İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.
  
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
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
