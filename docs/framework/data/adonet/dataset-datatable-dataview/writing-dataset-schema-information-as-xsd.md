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
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="6e7d2-103">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="6e7d2-103">Writing DataSet Schema Information as XSD</span></span>

<span data-ttu-id="6e7d2-104"><xref:System.Data.DataSet>XML şeması tanım dili (xsd) şemasının şemasını yazabilirsiniz, böylece onu BIR XML belgesinde veya bunlarla ilişkili verilerle birlikte aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-104">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="6e7d2-105">XML şeması bir dosyaya, akışa, bir <xref:System.Xml.XmlWriter> veya dizeye yazılabilir; türü kesin belirlenmiş bir **veri kümesi** oluşturmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-105">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="6e7d2-106">Türü kesin belirlenmiş **veri kümesi** nesneleri hakkında daha fazla bilgi için bkz. [Typed DataSet](typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="6e7d2-106">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="6e7d2-107">Bir tablo sütununun, nesnenin **ColumnMapping** ÖZELLIĞINI kullanarak XML şemasında nasıl temsil edileceğini belirtebilirsiniz <xref:System.Data.DataColumn> .</span><span class="sxs-lookup"><span data-stu-id="6e7d2-107">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="6e7d2-108">Daha fazla bilgi için, [veri kümesi IÇERIĞINI XML verileri olarak yazma](writing-dataset-contents-as-xml-data.md)Içindeki "sütunları XML öğelerine, özniteliklerine ve metne eşleme" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-108">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="6e7d2-109">Bir **veri kümesinin** şemasını bir dosyaya, akışa veya **XmlWriter**'a XML şeması olarak yazmak Için, **veri kümesinin** **WriteXmlSchema** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-109">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="6e7d2-110">**WriteXmlSchema** , sonuçta elde edilen XML şemasının hedefini belirten bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-110">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="6e7d2-111">Aşağıdaki kod örnekleri, bir **veri KÜMESININ** XML şemasının bir dosya adı ve bir nesne içeren bir dize geçirerek bir dosyaya nasıl yazılacağını göstermektedir <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="6e7d2-111">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="6e7d2-112">Bir **veri kümesinin** şemasını almak ve bir XML şeması dizesi olarak yazmak için aşağıdaki örnekte gösterildiği gibi **GetXmlSchema** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-112">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e7d2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7d2-113">See also</span></span>

- [<span data-ttu-id="6e7d2-114">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="6e7d2-114">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="6e7d2-115">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="6e7d2-115">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- [<span data-ttu-id="6e7d2-116">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="6e7d2-116">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="6e7d2-117">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="6e7d2-117">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="6e7d2-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e7d2-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
