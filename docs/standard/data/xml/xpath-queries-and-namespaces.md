---
title: "XPath sorguları ve ad alanları"
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
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eeed1594582765e5079aa1e3d82f95737a79d1f0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="a8b8f-102">XPath sorguları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="a8b8f-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="a8b8f-103">XPath sorguları bir XML belgesi, ad alanlarının farkında olduğundan ve ad alanı öneklerini öğe ve öznitelik adları nitelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="a8b8f-104">Bir ad alanı öneki ile öğe ve öznitelik adları niteleme belirli bir ad alanına ait düğümlere bir XPath sorgusu tarafından döndürülen düğümleri sınırlar.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="a8b8f-105">Örneğin, önek `books` eşleyen ad alanına `http://www.contoso.com/books`, ardından aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca seçer `book` ad alanındaki öğeler `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="a8b8f-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="a8b8f-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="a8b8f-107">Ad alanları bir XPath sorgusu kullanmak için bir nesne türetilmiş <xref:System.Xml.IXmlNamespaceResolver> gibi arabirim <xref:System.Xml.XmlNamespaceManager> sınıfı XPath sorgusu eklenecek öneki ve ad alanı URI'si ile yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="a8b8f-108"><xref:System.Xml.XmlNamespaceManager> Nesnesi, her aşağıdaki yollardan biriyle sorgusunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
-   <span data-ttu-id="a8b8f-109"><xref:System.Xml.XmlNamespaceManager> Nesnesidir varolan ile ilişkili <xref:System.Xml.XPath.XPathExpression> kullanarak nesne <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="a8b8f-110">Ayrıca yeni bir derleme <xref:System.Xml.XPath.XPathExpression> statik kullanarak nesne <xref:System.Xml.XPath.XPathExpression.Compile%2A> XPath ifadesi temsil eden bir dize alan yöntemi ve bir <xref:System.Xml.XmlNamespaceManager> nesne parametreleri ve yeni bir döndürür olarak <xref:System.Xml.XPath.XPathExpression> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
-   <span data-ttu-id="a8b8f-111"><xref:System.Xml.XmlNamespaceManager> Nesnenin kendisine geçirilen parametre olarak kabul bir <xref:System.Xml.XPath.XPathNavigator> sınıf XPath ifadesi temsil eden bir dize birlikte yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="a8b8f-112">Yöntemleri şunlardır <xref:System.Xml.XPath.XPathNavigator> nesneyi kabul sınıfı türetilen <xref:System.Xml.IXmlNamespaceResolver> bir parametre olarak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="a8b8f-113">Varsayılan Namespace</span><span class="sxs-lookup"><span data-stu-id="a8b8f-113">The Default Namespace</span></span>  
 <span data-ttu-id="a8b8f-114">Aşağıdaki XML belgesinde bildirmek için varsayılan ad alanı boş bir önek ile kullanılan `http://www.contoso.com/books` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="a8b8f-115">XPath boş önek davranır `null` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="a8b8f-116">Diğer bir deyişle, ad alanlarına eşlenen önekleri XPath sorguları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="a8b8f-117">Bu, varsayılan ad alanını olsa bile da, bir ad alanı bir XML belgesi karşı sorgulamak istiyorsanız, bunun için bir önek tanımlamak yapmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="a8b8f-118">Örneğin, yukarıdaki XPath XML belgesi için bir önek tanımlamadan sorgu `/books/book` herhangi bir sonuç döndürür değil.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="a8b8f-119">Bir ad değil, bazı düğümler ve bazı durumlarda bir varsayılan ad alanı belgelerle sorgulanırken Karışıklığı önlemek için bir önek bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="a8b8f-120">Aşağıdaki kod, varsayılan ad alanı için bir önek tanımlar ve tüm seçer `book` öğelerinden `http://www.contoso.com/books` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8b8f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8b8f-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="a8b8f-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="a8b8f-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="a8b8f-123">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="a8b8f-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="a8b8f-124">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a8b8f-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="a8b8f-125">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="a8b8f-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="a8b8f-126">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="a8b8f-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="a8b8f-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="a8b8f-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
