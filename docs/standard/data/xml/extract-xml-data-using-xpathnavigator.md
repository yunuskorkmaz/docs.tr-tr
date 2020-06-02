---
title: XPathNavigator Kullanarak XML Verilerini Ayıklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: e639931204a416c3cde87044730364a4f387799a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287772"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="7ebd5-102">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7ebd5-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="7ebd5-103">Microsoft .NET çerçevesindeki bir XML belgesini temsil etmenin birkaç farklı yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="7ebd5-104">Bu,, veya kullanarak, veya <xref:System.String> sınıflarını içerir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="7ebd5-105">XML belgesinin bu farklı temsilleri arasında geçmeyi kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> sınıfı, XML <xref:System.String> 'i bir, <xref:System.Xml.XmlReader> nesne veya nesne olarak ayıklamaya yönelik çeşitli yöntemler ve özellikler sağlar <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="7ebd5-106">Bir XPathNavigator 'yi dizeye Dönüştür</span><span class="sxs-lookup"><span data-stu-id="7ebd5-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="7ebd5-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>Sınıfının özelliği, <xref:System.Xml.XPath.XPathNavigator> tüm XML belgesi veya yalnızca tek bir düğüm ve onun alt düğümleri için biçimlendirme almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ebd5-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, bir düğümün yalnızca alt düğümlerinin işaretlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="7ebd5-109">Aşağıdaki kod örneği, bir nesnesinde bulunan bir XML belgesinin tamamını <xref:System.Xml.XPath.XPathNavigator> <xref:System.String> , tek bir düğüm ve onun alt düğümleri olarak nasıl kaydedileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="7ebd5-110">Bir XPathNavigator 'yi XmlReader 'ye dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="7ebd5-111">Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir nesnesine akışa almak için kullanılır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="7ebd5-112"><xref:System.Xml.XmlReader>Nesne geçerli düğüm ve onun alt düğümleri ile oluşturulduğunda <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği olarak ayarlanır <xref:System.Xml.ReadState.Initial> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="7ebd5-113"><xref:System.Xml.XmlReader>Nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında,, <xref:System.Xml.XmlReader> öğesinin geçerli düğümüne taşınır <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="7ebd5-114">Yeni <xref:System.Xml.XmlReader> nesne, xml ağacının sonuna ulaşılana kadar okumaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="7ebd5-115">Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döner `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği olarak ayarlanır <xref:System.Xml.ReadState.EndOfFile> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="7ebd5-116">Nesnenin <xref:System.Xml.XPath.XPathNavigator> konumu nesnenin oluşturulması veya taşınması tarafından değiştirilmez <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="7ebd5-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A>Yöntemi yalnızca bir öğe veya kök düğüm üzerinde konumlandırıldığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="7ebd5-118">Aşağıdaki örnek, <xref:System.Xml.XmlReader> bir nesnenin tüm XML belgesini <xref:System.Xml.XPath.XPathDocument> ve tek bir düğüm ve onun alt düğümlerini içeren bir nesnenin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="7ebd5-119">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="7ebd5-120">XPathNavigator 'yi XmlWriter 'a dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="7ebd5-121">Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir nesnesine akışa almak için kullanılır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="7ebd5-122"><xref:System.Xml.XPath.XPathNavigator>Nesnenin konumu nesnenin oluşturulmasıyla değiştirilmez <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="7ebd5-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="7ebd5-123">Aşağıdaki örnek, <xref:System.Xml.XmlWriter> bir nesnenin tüm XML belgesini <xref:System.Xml.XPath.XPathDocument> ve tek bir düğüm ve onun alt düğümlerini içeren bir nesnenin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="7ebd5-124">Örnek, `books.xml` Bu konunun önceki kısımlarında bulunan dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebd5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ebd5-125">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7ebd5-126">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-126">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7ebd5-127">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-127">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="7ebd5-128">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="7ebd5-129">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="7ebd5-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
