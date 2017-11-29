---
title: "XPathNavigator kullanarak XML veri ayıklamak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c42539db3750ebc2a4220ef776b89bbabe6aaca3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="ad9d2-102">XPathNavigator kullanarak XML veri ayıklamak</span><span class="sxs-lookup"><span data-stu-id="ad9d2-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="ad9d2-103">Microsoft .NET Framework XML belgesinde temsil etmek için birkaç farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="ad9d2-104">Bu kullanmayı da içeren bir <xref:System.String>, veya kullanarak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XPath.XPathDocument> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="ad9d2-105">Bu bir XML belgesi farklı sunumu arasında taşıma kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> sınıfı XML olarak ayıklanması için bir dizi yöntem ve özellikleri sağlar bir <xref:System.String>, <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XmlWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="ad9d2-106">Bir XPathNavigator bir dizeye dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ad9d2-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="ad9d2-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı, tüm XML belgenin biçimlendirme veya işaretleme yalnızca tek bir düğüme ve alt düğümleri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad9d2-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği yalnızca alt biçimlendirme düğümün öğelerinin alır.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="ad9d2-109">Aşağıdaki kod örneğinde yer alan tüm XML belgesi kaydedileceği gösterilmektedir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.String>, tek bir düğüme ve alt düğümlerini yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="ad9d2-110">Bir XPathNavigator XmlReader için Dönüştür</span><span class="sxs-lookup"><span data-stu-id="ad9d2-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="ad9d2-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi bir XML belgesi veya yalnızca tek bir düğüme ve alt düğümlerini tüm içeriğini akış için kullanılan bir <xref:System.Xml.XmlReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="ad9d2-112">Zaman <xref:System.Xml.XmlReader> nesne geçerli düğüme ve alt düğümlerini ile oluşturulur <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği ayarlanmış <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="ad9d2-113">Zaman <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında <xref:System.Xml.XmlReader> geçerli düğüme taşınır <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ad9d2-114">Yeni <xref:System.Xml.XmlReader> XML ağaç sonuna ulaşılana kadar okuma nesne devam eder.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="ad9d2-115">Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döndürür `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği ayarlanmış <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="ad9d2-116"><xref:System.Xml.XPath.XPathNavigator> Oluşturma veya hareketini nesnenin konumu değişmeden <xref:System.Xml.XmlReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="ad9d2-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi geçerli yalnızca bir öğe veya kök düğümde konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="ad9d2-118">Aşağıdaki örnekte nasıl alınacağını gösteren bir <xref:System.Xml.XmlReader> tüm XML içeren bir nesne belge bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüme ve alt düğümlerini yanı sıra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="ad9d2-119">Örnek alır `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="ad9d2-120">Bir XPathNavigator bir XmlWriter dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ad9d2-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="ad9d2-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Yöntemi bir XML belgesi veya yalnızca tek bir düğüme ve alt düğümlerini tüm içeriğini akış için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="ad9d2-122"><xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu tarafından oluşturulmasını değişmeden <xref:System.Xml.XmlWriter> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="ad9d2-123">Aşağıdaki örnekte nasıl alınacağını gösteren bir <xref:System.Xml.XmlWriter> tüm XML içeren bir nesne belge bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüme ve alt düğümlerini yanı sıra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="ad9d2-124">Örnek alır `books.xml` girdi olarak bu konunun önceki kısımlarında dosyası bulundu.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9d2-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-125">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ad9d2-126">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="ad9d2-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ad9d2-127">Düğüm kümesi Gezinti XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="ad9d2-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="ad9d2-128">Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme</span><span class="sxs-lookup"><span data-stu-id="ad9d2-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="ad9d2-129">XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme</span><span class="sxs-lookup"><span data-stu-id="ad9d2-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
