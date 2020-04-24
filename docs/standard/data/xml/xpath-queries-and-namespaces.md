---
title: XPath Sorguları ve Ad Alanları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: 91503ce0bffa1a9390432a51bff1ef10d80f563a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709783"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="8275a-102">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="8275a-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="8275a-103">XPath sorguları bir XML belgesindeki ad alanlarını algılar ve öğe ve öznitelik adlarını nitelemek için ad alanı öneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8275a-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="8275a-104">Bir ad alanı önekiyle niteleyen öğe ve öznitelik adları, bir XPath sorgusunun döndürdüğü düğümleri yalnızca belirli bir ad alanına ait olan düğümlere sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="8275a-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="8275a-105">Örneğin, önek `books` `http://www.contoso.com/books`ad alanıyla eşleniyorsa, aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca ad alanındaki `book` `http://www.contoso.com/books`öğeleri seçer.</span><span class="sxs-lookup"><span data-stu-id="8275a-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="8275a-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="8275a-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="8275a-107">Bir XPath sorgusunda ad alanlarını kullanmak için, <xref:System.Xml.IXmlNamespaceResolver> <xref:System.Xml.XmlNamespaceManager> sınıfı gibi arabiriminden türetilmiş bir nesne, ad alanı URI 'si ve XPath sorgusuna dahil edilecek ön ek ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8275a-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="8275a-108"><xref:System.Xml.XmlNamespaceManager> Nesnesi, aşağıdaki yolların her birinde sorgusunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8275a-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="8275a-109"><xref:System.Xml.XmlNamespaceManager> Nesnesi <xref:System.Xml.XPath.XPathExpression> , <xref:System.Xml.XPath.XPathExpression> nesnesinin <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi kullanılarak varolan bir nesneyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="8275a-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="8275a-110">Ayrıca, XPath ifadesini ve bir <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> <xref:System.Xml.XmlNamespaceManager> nesneyi parametreler olarak temsil eden bir dize alan ve yeni <xref:System.Xml.XPath.XPathExpression> bir nesne döndüren static yöntemi kullanarak yeni bir nesne derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8275a-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="8275a-111"><xref:System.Xml.XmlNamespaceManager> Nesnenin kendisi, XPath ifadesini temsil eden bir dize ile birlikte <xref:System.Xml.XPath.XPathNavigator> kabul eden bir sınıf yöntemine parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8275a-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="8275a-112">Aşağıda, <xref:System.Xml.IXmlNamespaceResolver> arabiriminden bir parametre olarak türetilmiş <xref:System.Xml.XPath.XPathNavigator> bir nesneyi kabul eden sınıfının yöntemleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8275a-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="8275a-113">Varsayılan ad alanı</span><span class="sxs-lookup"><span data-stu-id="8275a-113">The Default Namespace</span></span>  
 <span data-ttu-id="8275a-114">Aşağıdaki XML belgesinde, `http://www.contoso.com/books` ad alanını bildirmek için boş ön eki olan varsayılan ad alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8275a-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="8275a-115">XPath, boş öneki `null` ad alanı olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8275a-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="8275a-116">Diğer bir deyişle, XPath sorgularında yalnızca ad alanlarına eşlenmiş önekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8275a-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="8275a-117">Bu, varsayılan ad alanı olsa bile bir XML belgesinde bir ad alanı üzerinde sorgu yapmak istiyorsanız, bunun için bir ön ek tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8275a-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="8275a-118">Örneğin, yukarıdaki XML belgesi için bir ön ek tanımlamadan, XPath sorgusu `/books/book` herhangi bir sonuç döndürmez.</span><span class="sxs-lookup"><span data-stu-id="8275a-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="8275a-119">Bir önek, bir ad alanında olmayan bazı düğümlerle ve bazıları varsayılan bir ad alanında yer alan bir düğüm sorgulanırken belirsizlik oluşmasını engellemek için bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8275a-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="8275a-120">Aşağıdaki kod, varsayılan ad alanı için bir ön ek tanımlar ve `book` `http://www.contoso.com/books` ad alanındaki tüm öğeleri seçer.</span><span class="sxs-lookup"><span data-stu-id="8275a-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8275a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8275a-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="8275a-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="8275a-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="8275a-123">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="8275a-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="8275a-124">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="8275a-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="8275a-125">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="8275a-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="8275a-126">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="8275a-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="8275a-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="8275a-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
