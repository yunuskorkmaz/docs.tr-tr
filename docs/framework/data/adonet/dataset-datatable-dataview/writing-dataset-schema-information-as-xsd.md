---
title: "Veri kümesi şema bilgileri XSD olarak yazma"
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
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dde8a16ee0fbd86dacf6125c9a02209a794a5b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="fcccb-102">Veri kümesi şema bilgileri XSD olarak yazma</span><span class="sxs-lookup"><span data-stu-id="fcccb-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="fcccb-103">Şeması yazabilirsiniz bir <xref:System.Data.DataSet> olarak XML Şeması Tanım Dili (XSD) şeması, böylece, olan veya olmayan bir XML belgesi ilgili veri taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="fcccb-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="fcccb-104">XML şeması bir dosyaya, bir akış yazılabilir bir <xref:System.Xml.XmlWriter>, veya bir dize; kesin türü belirtilmiş oluşturmada yararlıdır **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fcccb-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="fcccb-105">Hakkında daha fazla bilgi için kesin türü belirtilmiş **DataSet** nesneleri bkz [yazılan veri kümeleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="fcccb-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="fcccb-106">Bir tablo sütunu XML Şeması nasıl temsil belirtebilirsiniz kullanarak **ColumnMapping** özelliği <xref:System.Data.DataColumn> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fcccb-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="fcccb-107">Daha fazla bilgi için bkz: "XML öğeleri, öznitelikleri ve metin sütunları eşleme" [XML verileri olarak yazma DataSet içeriği](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="fcccb-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="fcccb-108">Şeması yazmak için bir **DataSet** bir dosyaya XML şeması olarak akışı veya **XmlWriter**, kullanın **WriteXmlSchema** yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fcccb-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="fcccb-109">**WriteXmlSchema** sonuç XML Şeması hedef belirten bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="fcccb-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="fcccb-110">Aşağıdaki kod örnekleri XML Şeması yazma göstermektedir bir **DataSet** bir dosya adı içeren bir dize geçirerek bir dosyaya ve <xref:System.IO.StreamWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="fcccb-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="fcccb-111">Şeması almak için bir **DataSet** ve bir XML Şeması dize olarak okuma ve yazma, kullanma **GetXmlSchema** aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fcccb-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcccb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcccb-112">See Also</span></span>  
 [<span data-ttu-id="fcccb-113">Bir veri kümesini XML kullanma</span><span class="sxs-lookup"><span data-stu-id="fcccb-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="fcccb-114">XML verileri olarak DataSet içeriğini yazma</span><span class="sxs-lookup"><span data-stu-id="fcccb-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="fcccb-115">Yazılan veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="fcccb-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="fcccb-116">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="fcccb-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="fcccb-117">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fcccb-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
