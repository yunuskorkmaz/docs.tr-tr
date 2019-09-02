---
title: XSD Olarak DataSet Schema Bilgilerini Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f9664d8e7bc221da68492140f30419ea8fb0d316
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204369"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD Olarak DataSet Schema Bilgilerini Yazma
XML şeması tanım dili (xsd) <xref:System.Data.DataSet> şemasının şemasını yazabilirsiniz, böylece onu bir XML belgesinde veya bunlarla ilişkili verilerle birlikte aktarabilirsiniz. XML şeması bir dosyaya, akışa, bir <xref:System.Xml.XmlWriter>veya dizeye yazılabilir; türü kesin belirlenmiş bir **veri kümesi**oluşturmak için kullanışlıdır. Türü kesin belirlenmiş **veri kümesi** nesneleri hakkında daha fazla bilgi için bkz. [Typed DataSet](typed-datasets.md).  
  
 Bir tablo sütununun, <xref:System.Data.DataColumn> nesnenin **ColumnMapping** özelliğini kullanarak XML şemasında nasıl temsil edileceğini belirtebilirsiniz. Daha fazla bilgi için, [veri kümesi IÇERIĞINI XML verileri olarak yazma](writing-dataset-contents-as-xml-data.md)Içindeki "sütunları XML öğelerine, özniteliklerine ve metne eşleme" konusuna bakın.  
  
 Bir **veri kümesinin** şemasını bir dosyaya, akışa veya **XmlWriter**'a XML şeması olarak yazmak Için, **veri kümesinin** **WriteXmlSchema** yöntemini kullanın. **WriteXmlSchema** , sonuçta elde edilen XML şemasının hedefini belirten bir parametre alır. Aşağıdaki kod örnekleri, bir **veri kümesinin** XML şemasının bir dosya adı ve bir <xref:System.IO.StreamWriter> nesne içeren bir dize geçirerek bir dosyaya nasıl yazılacağını göstermektedir.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
