---
title: XSD Olarak DataSet Schema Bilgilerini Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784173"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="1f34f-102">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="1f34f-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="1f34f-103">XML şeması tanım dili (xsd) <xref:System.Data.DataSet> şemasının şemasını yazabilirsiniz, böylece onu bir XML belgesinde veya bunlarla ilişkili verilerle birlikte aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f34f-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="1f34f-104">XML şeması bir dosyaya, akışa, bir <xref:System.Xml.XmlWriter>veya dizeye yazılabilir; türü kesin belirlenmiş bir **veri kümesi**oluşturmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f34f-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="1f34f-105">Türü kesin belirlenmiş **veri kümesi** nesneleri hakkında daha fazla bilgi için bkz. [Typed DataSet](typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="1f34f-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="1f34f-106">Bir tablo sütununun, <xref:System.Data.DataColumn> nesnenin **ColumnMapping** özelliğini kullanarak XML şemasında nasıl temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f34f-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="1f34f-107">Daha fazla bilgi için, [veri kümesi IÇERIĞINI XML verileri olarak yazma](writing-dataset-contents-as-xml-data.md)Içindeki "sütunları XML öğelerine, özniteliklerine ve metne eşleme" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="1f34f-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="1f34f-108">Bir **veri kümesinin** şemasını bir dosyaya, akışa veya **XmlWriter**'a XML şeması olarak yazmak Için, **veri kümesinin** **WriteXmlSchema** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f34f-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="1f34f-109">**WriteXmlSchema** , sonuçta elde edilen XML şemasının hedefini belirten bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="1f34f-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="1f34f-110">Aşağıdaki kod örnekleri, bir **veri kümesinin** XML şemasının bir dosya adı ve bir <xref:System.IO.StreamWriter> nesne içeren bir dize geçirerek bir dosyaya nasıl yazılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1f34f-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="1f34f-111">Bir **veri kümesinin** şemasını almak ve bir XML şeması dizesi olarak yazmak için aşağıdaki örnekte gösterildiği gibi **GetXmlSchema** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f34f-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f34f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f34f-112">See also</span></span>

- [<span data-ttu-id="1f34f-113">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="1f34f-113">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1f34f-114">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="1f34f-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="1f34f-115">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="1f34f-115">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="1f34f-116">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1f34f-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1f34f-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f34f-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
