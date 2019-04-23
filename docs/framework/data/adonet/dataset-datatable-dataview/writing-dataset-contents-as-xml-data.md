---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: dae044a9d7802e858f1f24dd4aa0f1de8f6cba7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158958"
---
# <a name="writing-dataset-contents-as-xml-data"></a>XML Verileri Olarak DataSet İçeriği Yazma
ADO.NET içinde bir XML temsilini yazabileceğiniz bir <xref:System.Data.DataSet>, ile veya olmadan şeması. XML ile satır içi şema bilgileri ise XML Şeması Tanım Dili (XSD) kullanarak yazılır. Tablo tanımları şema içeriyor <xref:System.Data.DataSet> ilişki ve kısıtlama tanımları yanı sıra.  
  
 Olduğunda bir <xref:System.Data.DataSet> XML verileri, satır olarak yazılır <xref:System.Data.DataSet> geçerli sürümlerine yazılır. Ancak, <xref:System.Data.DataSet> böylece hem geçerli hem de satır özgün değerlerine dahil edilecek bir DiffGram da yazılabilir.  
  
 XML gösterimini <xref:System.Data.DataSet> bir dosyaya, bir akışa yazılabilir bir **XmlWriter**, veya bir dize. Bu seçenek, XML gösterimini nasıl aktarım için büyük esneklik sağlar <xref:System.Data.DataSet>. XML gösterimini elde etmek için <xref:System.Data.DataSet> bir dize kullanmak **GetXml** aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** XML gösterimini döndürür <xref:System.Data.DataSet> şema bilgileri olmadan. Şema bilgileri yazılacak <xref:System.Data.DataSet> (olarak XML şema) kullanan bir dizeye **GetXmlSchema**.  
  
 Yazılacak bir <xref:System.Data.DataSet> bir dosya için akışı veya **XmlWriter**, kullanın **WriteXml** yöntemi. Geçirmek için ilk parametre **WriteXml** hedefi olan XML çıktısı. Örneğin, bir dosya adı içeren bir dizeyi geçirmek bir **System.IO.TextWriter** nesne ve benzeri. İsteğe bağlı ikinci parametresi, geçirdiğiniz bir **XmlWriteMode** nasıl yazılacak XML çıktısı olduğunu belirtmek için.  
  
 Aşağıdaki tabloda ilişkin seçenekler gösterilir **XmlWriteMode**.  
  
|XmlWriteMode option|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Geçerli içeriği Yazar <xref:System.Data.DataSet> olmadan bir XML Şeması XML verileri olarak. Bu varsayılandır.|  
|**WriteSchema**|Geçerli içeriği Yazar <xref:System.Data.DataSet> XML Şeması satır içi olarak ilişkisel yapı ile XML verileri olarak.|  
|**DiffGram**|Tüm Yazar <xref:System.Data.DataSet> bir DiffGram özgün ve geçerli değerleri dahil. Daha fazla bilgi için [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Bir XML temsilini yazılırken bir <xref:System.Data.DataSet> içeren **DataRelation** nesneler, büyük olasılıkla her ilişkinin ilgili üst öğeleri içinde iç içe geçmiş alt öğe satırları için elde edilen XML Environment. Bunu gerçekleştirmek için ayarlanmış **iç içe** özelliği **DataRelation** için **true** eklediğinizde **DataRelation** için<xref:System.Data.DataSet>. Daha fazla bilgi için [iç içe DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 XML gösterimini yazma konusunda iki örnek aşağıda verilmiştir bir <xref:System.Data.DataSet> dosyaya. İlk örnek, bir dize olarak elde edilen XML dosyası adını geçirir. **WriteXml**. İkinci örnek geçen bir **System.IO.StreamWriter** nesne.  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>XML öğeleri, öznitelikleri ve metin sütunları eşleme  
 Bir tablo sütunu XML nasıl temsil edildiğini belirtebilirsiniz kullanarak **Columnmapping'in** özelliği **DataColumn** nesne. Aşağıdaki tabloda farklı gösterilmektedir **MappingType** değerleri **Columnmapping'in** bir tablo sütunu ve elde edilen XML özelliği.  
  
|MappingType değeri|Açıklama|  
|-----------------------|-----------------|  
|**Öğe**|Bu varsayılandır. Sütun, burada ColumnName öğe adı, sütunun içeriğine öğenin metin olarak yazılmış bir XML öğesi olarak yazılır. Örneğin:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Öznitelik**|Sütun XML öğesi geçerli satıra burada ColumnName özniteliğin adını ve sütun içeriğini öznitelik değeri olarak yazılmış bir XML özniteliği olarak yazılır. Örneğin:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Bir sütunun içeriğine metin XML öğesi geçerli satır olarak yazılır. Örneğin:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Unutmayın **SimpleContent** sahip bir tablo için bir sütun ayarlanamaz **öğesi** sütunları veya iç içe geçmiş ilişkileri.|  
|**Gizli**|Sütun XML çıktısında yazılmaz.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [DataRelations’ı İç İçe Yerleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [XSD Olarak DataSet Schema Bilgilerini Yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
