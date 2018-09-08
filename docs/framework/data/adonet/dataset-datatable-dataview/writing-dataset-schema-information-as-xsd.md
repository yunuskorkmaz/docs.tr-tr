---
title: XSD olarak DataSet Schema bilgilerini yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192515"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="fe255-102">XSD olarak DataSet Schema bilgilerini yazma</span><span class="sxs-lookup"><span data-stu-id="fe255-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="fe255-103">Şemasını yazabileceğiniz bir <xref:System.Data.DataSet> olarak XML Şeması Tanım Dili (XSD) şemaya, böylece onu içeren veya içermeyen bir XML belgesi ilgili verileri taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="fe255-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="fe255-104">XML şeması bir dosyaya, bir akışa yazılabilir bir <xref:System.Xml.XmlWriter>, veya bir dize; türü kesin belirlenmiş oluşturmada yararlıdır **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="fe255-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="fe255-105">Hakkında daha fazla bilgi için türü kesin belirlenmiş **veri kümesi** nesneleri bkz [yazılan veri kümeleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="fe255-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="fe255-106">Bir tablo sütunu XML Şeması ' nasıl temsil edildiğini belirtebilirsiniz kullanarak **Columnmapping'in** özelliği <xref:System.Data.DataColumn> nesne.</span><span class="sxs-lookup"><span data-stu-id="fe255-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="fe255-107">Daha fazla bilgi için bkz: "Metin XML öğeleri ve öznitelikleri sütun eşleme" [XML verileri olarak DataSet içeriği yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="fe255-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="fe255-108">Şemasını yazmak için bir **veri kümesi** bir dosyaya bir XML şeması olarak akışı veya **XmlWriter**, kullanın **WriteXmlSchema** yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="fe255-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="fe255-109">**WriteXmlSchema** elde edilen XML Şeması hedef belirten bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="fe255-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="fe255-110">Aşağıdaki kod örnekleri XML şemasını yazma işlemini göstermek bir **veri kümesi** bir dosyaya, bir dosya adı içeren bir dize geçirerek ve <xref:System.IO.StreamWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="fe255-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="fe255-111">Şemasını almak için bir **veri kümesi** ve bir XML Şeması dize olarak yazın, kullanın **GetXmlSchema** yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fe255-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe255-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe255-112">See Also</span></span>  
 [<span data-ttu-id="fe255-113">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="fe255-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="fe255-114">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="fe255-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="fe255-115">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="fe255-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="fe255-116">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="fe255-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="fe255-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fe255-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
