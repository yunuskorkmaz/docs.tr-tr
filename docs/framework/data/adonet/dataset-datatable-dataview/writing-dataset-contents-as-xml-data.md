---
title: Veri kümesi Içeriğini XML verileri olarak yazma
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
# <a name="writing-dataset-contents-as-xml-data"></a>Veri kümesi Içeriğini XML verileri olarak yazma
ADO.NET ' de, şemasına sahip veya olmayan <xref:System.Data.DataSet> ' ın bir XML gösterimini yazabilirsiniz. Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır. Şema <xref:System.Data.DataSet> ' ın tablo tanımlarını ve ilişki ve kısıtlama tanımlarını içerir.  
  
 Bir <xref:System.Data.DataSet>, XML verisi olarak yazıldığında, <xref:System.Data.DataSet> ' deki satırlar geçerli sürümlerinde yazılır. Ancak, <xref:System.Data.DataSet> ' ın hem geçerli hem de orijinal değerlerinin dahil edilmesini sağlamak için bir DiffGram olarak yazılabilir.  
  
 @No__t-0 ' ın XML temsili bir dosyaya, akışa, bir **XmlWriter**'a veya dizeye yazılabilir. Bu seçimler <xref:System.Data.DataSet> ' ın XML gösterimini taşımanın harika bir esnekliğini sağlar. @No__t-0 ' ın XML gösterimini bir dize olarak almak için, aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** şema bilgisi olmadan <xref:System.Data.DataSet> ' in XML gösterimini döndürür. @No__t-0 ' dan (XML şeması olarak) şema bilgilerini bir dizeye yazmak için **GetXmlSchema**kullanın.  
  
 Bir dosyaya, akışa veya **XmlWriter**'a bir @no__t yazmak için **WriteXml** yöntemini kullanın. **WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir. Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin. XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.  
  
 Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.  
  
|XmlWriteMode seçeneği|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|@No__t-0 ' ın geçerli içeriğini xml şeması olmadan XML verisi olarak yazar. Bu varsayılandır.|  
|**WriteSchema seçeneğine ayarlayın**|@No__t-0 ' ın geçerli içeriğini, ilişkisel yapıda satır içi XML şeması olarak XML verisi olarak yazar.|  
|**Içeriyor**|Özgün ve geçerli değerler dahil olmak üzere tüm <xref:System.Data.DataSet> ' ı bir DiffGram olarak yazar. Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).|  
  
 **DataRelation** nesneleri içeren <xref:System.Data.DataSet> ' ın bir XML temsilini yazarken, sonuçta elde edilen XML 'nin ilgili üst öğelerinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz. Bunu gerçekleştirmek için, **DataRelation** 'ı <xref:System.Data.DataSet> ' e eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın. Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).  
  
 Aşağıda bir <xref:System.Data.DataSet> ' ın XML gösteriminin bir dosyaya nasıl yazılacağı hakkında iki örnek verilmiştir. İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir. İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.
  
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
|**Dosyalarında**|Bu varsayılandır. Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır. Örnek:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Özniteliğe**|Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır. Örnek:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**'Dir**|Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır. Örnek:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> **Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.|  
|**Lene**|Sütun XML çıktısında yazılmadı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir veri kümesinde XML kullanma](using-xml-in-a-dataset.md)
- [DiffGram](diffgrams.md)
- [DataRelation 'ı iç içe geçirme](nesting-datarelations.md)
- [Veri kümesi şema bilgilerini XSD olarak yazma](writing-dataset-schema-information-as-xsd.md)
- [Veri kümeleri, DataTable ve DataView](index.md)
- [ADO.NET genel bakış](../ado-net-overview.md)
