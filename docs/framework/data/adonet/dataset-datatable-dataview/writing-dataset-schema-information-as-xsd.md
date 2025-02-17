---
description: 'Hakkında daha fazla bilgi edinin: veri kümesi şema bilgilerini XSD olarak yazma'
title: XSD Olarak DataSet Schema Bilgilerini Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: e05188c74ca21e73ee5151da817e143102640a13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651359"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD Olarak DataSet Schema Bilgilerini Yazma

<xref:System.Data.DataSet>XML şeması tanım dili (xsd) şemasının şemasını yazabilirsiniz, böylece onu BIR XML belgesinde veya bunlarla ilişkili verilerle birlikte aktarabilirsiniz. XML şeması bir dosyaya, akışa, bir <xref:System.Xml.XmlWriter> veya dizeye yazılabilir; türü kesin belirlenmiş bir **veri kümesi** oluşturmak için kullanışlıdır. Türü kesin belirlenmiş **veri kümesi** nesneleri hakkında daha fazla bilgi için bkz. [Typed DataSet](typed-datasets.md).  
  
 Bir tablo sütununun, nesnenin **ColumnMapping** ÖZELLIĞINI kullanarak XML şemasında nasıl temsil edileceğini belirtebilirsiniz <xref:System.Data.DataColumn> . Daha fazla bilgi için, [veri kümesi IÇERIĞINI XML verileri olarak yazma](writing-dataset-contents-as-xml-data.md)Içindeki "sütunları XML öğelerine, özniteliklerine ve metne eşleme" konusuna bakın.  
  
 Bir **veri kümesinin** şemasını bir dosyaya, akışa veya **XmlWriter**'a XML şeması olarak yazmak Için, **veri kümesinin** **WriteXmlSchema** yöntemini kullanın. **WriteXmlSchema** , sonuçta elde edilen XML şemasının hedefini belirten bir parametre alır. Aşağıdaki kod örnekleri, bir **veri KÜMESININ** XML şemasının bir dosya adı ve bir nesne içeren bir dize geçirerek bir dosyaya nasıl yazılacağını göstermektedir <xref:System.IO.StreamWriter> .  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Bir **veri kümesinin** şemasını almak ve bir XML şeması dizesi olarak yazmak için aşağıdaki örnekte gösterildiği gibi **GetXmlSchema** yöntemini kullanın.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [XML Verileri Olarak DataSet İçeriği Yazma](writing-dataset-contents-as-xml-data.md)
- [Türü Belirtilmiş DataSets](typed-datasets.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
