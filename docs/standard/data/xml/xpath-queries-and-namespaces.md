---
title: XPath sorguları ve ad alanları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b11ac80b671c345768da23d2b51d2333c228aaeb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208601"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="da1e7-102">XPath sorguları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="da1e7-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="da1e7-103">XPath sorguları, XML belgesinde ad alanlarının farkındayız ve ad alanı öneklerini öğe ve öznitelik adları nitelemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da1e7-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="da1e7-104">Ad alanı öneki öğe ve öznitelik adlarını niteleme yalnızca belirli bir ad alanına ait düğümleri bir XPath sorgusu tarafından döndürülen düğümleri sınırlar.</span><span class="sxs-lookup"><span data-stu-id="da1e7-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="da1e7-105">Örneğin, ön eki `books` eşleyen ad alanına `http://www.contoso.com/books`, ardından aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca seçer `book` ad alanındaki öğeler `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="da1e7-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="da1e7-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="da1e7-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="da1e7-107">Bir XPath sorgusu ad alanları kullanmak için bir nesne türetilen <xref:System.Xml.IXmlNamespaceResolver> gibi arabirim <xref:System.Xml.XmlNamespaceManager> sınıfı XPath sorgusundaki eklenecek önek ve ad alanı URI ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="da1e7-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="da1e7-108"><xref:System.Xml.XmlNamespaceManager> Sorguda aşağıdaki yollardan biriyle her nesne kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da1e7-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
-   <span data-ttu-id="da1e7-109"><xref:System.Xml.XmlNamespaceManager> Nesnedir varolan ile ilişkili <xref:System.Xml.XPath.XPathExpression> kullanarak nesne <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> nesne.</span><span class="sxs-lookup"><span data-stu-id="da1e7-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="da1e7-110">Ayrıca yeni bir derleme <xref:System.Xml.XPath.XPathExpression> 'using static nesne <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi XPath ifadesi temsil eden bir dize alır ve bir <xref:System.Xml.XmlNamespaceManager> nesnesi parametrelerini ve yeni bir döndürür olarak <xref:System.Xml.XPath.XPathExpression> nesne.</span><span class="sxs-lookup"><span data-stu-id="da1e7-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
-   <span data-ttu-id="da1e7-111"><xref:System.Xml.XmlNamespaceManager> Nesnesinin kendisi bir kabul etmek için parametre olarak geçirilir <xref:System.Xml.XPath.XPathNavigator> sınıfı XPath ifadesi temsil eden bir dize ile birlikte yöntemi.</span><span class="sxs-lookup"><span data-stu-id="da1e7-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="da1e7-112">Yöntemleri şunlardır <xref:System.Xml.XPath.XPathNavigator> kabul eden bir nesne sınıfı türetilen <xref:System.Xml.IXmlNamespaceResolver> arabirimi bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="da1e7-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="da1e7-113">Varsayılan Namespace</span><span class="sxs-lookup"><span data-stu-id="da1e7-113">The Default Namespace</span></span>  
 <span data-ttu-id="da1e7-114">Aşağıdaki XML belgesinde varsayılan ad alanı ön eki boş bildirmek için kullanılan `http://www.contoso.com/books` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="da1e7-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="da1e7-115">XPath boş önek olarak değerlendirir `null` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="da1e7-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="da1e7-116">Diğer bir deyişle, yalnızca ad alanlarına eşlenen ön ekleri XPath sorguları içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da1e7-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="da1e7-117">Bu, varsayılan ad alanı olsa da, bir ad alanı bir XML belgesi karşı sorgulamak istiyorsanız, bunun için bir ön eki tanımlamak gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da1e7-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="da1e7-118">Örneğin, yukarıdaki XPath XML belgesi için bir önek tanımlamadan sorgu `/books/book` herhangi bir sonuç döndürmek değil.</span><span class="sxs-lookup"><span data-stu-id="da1e7-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="da1e7-119">Belgeler, bir ad alanındaki bazı düğümler ve bazı durumlarda bir varsayılan ad alanı sorgulanırken belirsizlik önlemek için bir önek bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da1e7-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="da1e7-120">Aşağıdaki kod bir varsayılan ad alanı öneki tanımlar ve tüm seçer `book` öğelerden `http://www.contoso.com/books` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="da1e7-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da1e7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da1e7-121">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="da1e7-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="da1e7-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="da1e7-123">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="da1e7-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="da1e7-124">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="da1e7-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="da1e7-125">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="da1e7-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="da1e7-126">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="da1e7-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="da1e7-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="da1e7-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
