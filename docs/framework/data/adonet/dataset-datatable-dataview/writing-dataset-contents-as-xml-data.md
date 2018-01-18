---
title: "XML verileri olarak DataSet içeriğini yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b1250d616ad5835fccd1a3acbf0b8a759c34181
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-contents-as-xml-data"></a>XML verileri olarak DataSet içeriğini yazma
ADO.NET bir XML temsili yazabilen bir <xref:System.Data.DataSet>, ile veya olmadan şemasına. Şema bilgileri XML ile birlikte satır içi ise XML Şeması Tanım Dili (XSD) kullanılarak yazılır. Tablo tanımları bir şema içeriyor <xref:System.Data.DataSet> ilişki ve kısıtlama tanımları yanı sıra.  
  
 Zaman bir <xref:System.Data.DataSet> XML verileri, satırları olarak yazılmış <xref:System.Data.DataSet> geçerli sürümlerine yazılır. Ancak, <xref:System.Data.DataSet> böylece geçerli ve özgün değerleri satır eklenecek DiffGram da yazılabilir.  
  
 XML gösterimini <xref:System.Data.DataSet> bir dosyaya, bir akış yazılabilir bir **XmlWriter**, veya bir dize. Bu seçenekler XML gösterimini nasıl taşıma için büyük esneklik sağlar <xref:System.Data.DataSet>. XML gösterimini almak için <xref:System.Data.DataSet> bir dize kullanmak **GetXml** aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** XML gösterimini döndürür <xref:System.Data.DataSet> şema bilgileri olmadan. Şema bilgileri yazmak için <xref:System.Data.DataSet> (olarak XML Şeması) bir dizeye kullanmak **GetXmlSchema**.  
  
 Yazmak için bir <xref:System.Data.DataSet> bir dosyaya akışı veya **XmlWriter**, kullanın **WriteXml** yöntemi. Geçirdiğiniz için ilk parametre **WriteXml** XML çıktı hedefi. Örneğin, bir dosya adı içeren bir dizeyi geçirmek bir **System.IO.TextWriter** nesne ve benzeri. Bir isteğe bağlı ikinci parametresi, geçirdiğiniz bir **XmlWriteMode** nasıl yazılacak XML çıktısı olduğunu belirtmek için.  
  
 Aşağıdaki tabloda seçeneklerini gösterir **XmlWriteMode**.  
  
|XmlWriteMode option|Açıklama|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Geçerli içeriğini Yazar <xref:System.Data.DataSet> bir XML Şeması olmadan XML verileri olarak. Bu varsayılandır.|  
|**WriteSchema**|Geçerli içeriğini Yazar <xref:System.Data.DataSet> XML Şeması satır içi olarak ilişkisel yapısı ile XML verileri olarak.|  
|**DiffGram**|Tüm Yazar <xref:System.Data.DataSet> bir DiffGram özgün geçerli değerler dahil olmak üzere. Daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Bir XML temsili yazılırken bir <xref:System.Data.DataSet> içeren **DataRelation** nesneleri büyük olasılıkla istediğiniz kendi ilgili üst öğeler içinde iç içe geçmiş her ilişkinin alt satır olması için sonuç XML. Bunu gerçekleştirmek için ayarlanmış **iç içe** özelliği **DataRelation** için **true** eklediğinizde **DataRelation** için<xref:System.Data.DataSet>. Daha fazla bilgi için bkz: [iç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 XML gösterimini yazmak iki örnekleri verilmiştir bir <xref:System.Data.DataSet> bir dosyaya. İlk örnek için sonuç XML dosya adı bir dize olarak geçirir. **WriteXml**. İkinci örnek geçirmeden bir **System.IO.StreamWriter** nesnesi.  
  
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
 Bir tablo sütunu XML'de nasıl temsil belirtebilirsiniz kullanarak **ColumnMapping** özelliği **DataColumn** nesnesi. Aşağıdaki tabloda farklı gösterilmektedir **MappingType** değerleri **ColumnMapping** bir tablo sütunu ve sonuçta elde edilen XML özelliği.  
  
|MappingType değeri|Açıklama|  
|-----------------------|-----------------|  
|**Öğesi**|Bu varsayılandır. Sütun, burada ColumnName öğenin adını ve sütun içeriğini öğesinin metin olarak yazılan bir XML öğesi olarak yazılır. Örneğin:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Özniteliği**|Sütun XML öğesi burada ColumnName özniteliğin adını ve sütun içeriğini öznitelik değeri olarak yazılan geçerli satır için XML özniteliği olarak yazılır. Örneğin:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Sütunun içeriğine metin XML öğesi geçerli satır için olarak yazılır. Örneğin:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Unutmayın **SimpleContent** sahip bir tablo için bir sütun ayarlanamaz **öğesi** sütunları veya iç içe ilişkiler.|  
|**Hidden**|Sütun XML çıktısında yazılmaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [DataRelations’ı İç İçe Yerleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [XSD Olarak DataSet Schema Bilgilerini Yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
