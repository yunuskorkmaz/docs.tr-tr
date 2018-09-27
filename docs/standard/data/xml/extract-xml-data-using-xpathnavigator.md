---
title: XPathNavigator kullanarak XML verilerini ayıklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d838f3d9f4c9400fbbef0fb24f5275eff2038c49
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232683"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="10174-102">XPathNavigator kullanarak XML verilerini ayıklama</span><span class="sxs-lookup"><span data-stu-id="10174-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="10174-103">Microsoft .NET Framework XML belgesinde temsil etmek için birkaç farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="10174-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="10174-104">Bu kullanarak içerir bir <xref:System.String>, kullanarak veya <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XPath.XPathDocument> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="10174-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="10174-105">Bu bir XML belgesi farklı temsilleri arasında taşıma kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> XML olarak ayıklanmasında sınıfı bir dizi yöntem ve özellik sağlar bir <xref:System.String>, <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XmlWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="10174-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="10174-106">Bir XPathNavigator bir dizeye Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10174-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="10174-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı, tüm XML belgesi işaretleme veya biçimlendirme yalnızca tek bir düğüm ve onun alt düğümleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10174-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10174-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği yalnızca alt biçimlendirme düğümünün düğüm alır.</span><span class="sxs-lookup"><span data-stu-id="10174-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="10174-109">Aşağıdaki kod örneğinde yer alan tüm bir XML belgesi kaydetmek gösterilmiştir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.String>, yanı sıra tek bir düğüm ve onun alt düğümleri.</span><span class="sxs-lookup"><span data-stu-id="10174-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="10174-110">XmlReader'a bir XPathNavigator Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10174-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="10174-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi akışını bir XML belgesi veya tek bir düğüm ve onun alt düğümleri için tüm içeriği için kullanılan bir <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="10174-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="10174-112">Zaman <xref:System.Xml.XmlReader> nesne geçerli düğüm ve onun alt düğümleri ile oluşturulan <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="10174-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="10174-113">Zaman <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında <xref:System.Xml.XmlReader> geçerli düğüme taşınır <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="10174-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="10174-114">Yeni <xref:System.Xml.XmlReader> nesne XML ağacı sonuna ulaşıncaya kadar okuyun devam eder.</span><span class="sxs-lookup"><span data-stu-id="10174-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="10174-115">Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döndürür `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="10174-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="10174-116"><xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu oluşturma ve hareketini tarafından değiştirilmeden <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="10174-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="10174-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi, yalnızca bir öğe veya kök düğümde getirildiğinde geçerli.</span><span class="sxs-lookup"><span data-stu-id="10174-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="10174-118">Aşağıdaki örnek nasıl alınacağını gösterir. bir <xref:System.Xml.XmlReader> nesnesi içeren tüm XML belge içinde bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüm ve onun alt düğümleri yanı sıra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="10174-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 <span data-ttu-id="10174-119">Örnek alan `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="10174-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="10174-120">Bir XPathNavigator XmlWriter için dönüştürme</span><span class="sxs-lookup"><span data-stu-id="10174-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="10174-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Yöntemi akışını bir XML belgesi veya tek bir düğüm ve onun alt düğümleri için tüm içeriği için kullanılan bir <xref:System.Xml.XmlWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="10174-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="10174-122"><xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu tarafından oluşturulmasını değişmeden <xref:System.Xml.XmlWriter> nesne.</span><span class="sxs-lookup"><span data-stu-id="10174-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="10174-123">Aşağıdaki örnek nasıl alınacağını gösterir. bir <xref:System.Xml.XmlWriter> nesnesi içeren tüm XML belge içinde bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüm ve onun alt düğümleri yanı sıra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="10174-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 <span data-ttu-id="10174-124">Örnek alan `books.xml` girdi olarak bu konudaki daha önce dosya bulundu.</span><span class="sxs-lookup"><span data-stu-id="10174-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10174-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10174-125">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="10174-126">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="10174-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="10174-127">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="10174-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="10174-128">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="10174-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="10174-129">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="10174-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
