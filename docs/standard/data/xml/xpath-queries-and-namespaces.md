---
title: XPath Sorguları ve Ad Alanları
description: Ad alanları & XPath sorguları hakkında bilgi edinin. XPath sorguları bir XML belgesindeki ad alanlarını bilir &, öğe & öznitelik adlarını nitelemek için ad alanı öneklerini kullanabilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: e8533d372a747432201dfbc4d879ecd3fbceaf8e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769255"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="98b36-104">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="98b36-104">XPath Queries and Namespaces</span></span>
<span data-ttu-id="98b36-105">XPath sorguları bir XML belgesindeki ad alanlarını algılar ve öğe ve öznitelik adlarını nitelemek için ad alanı öneklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="98b36-105">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="98b36-106">Bir ad alanı önekiyle niteleyen öğe ve öznitelik adları, bir XPath sorgusunun döndürdüğü düğümleri yalnızca belirli bir ad alanına ait olan düğümlere sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="98b36-106">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="98b36-107">Örneğin, önek `books` ad alanıyla eşleniyorsa `http://www.contoso.com/books` , aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca `book` ad alanındaki öğeleri seçer `http://www.contoso.com/books` .</span><span class="sxs-lookup"><span data-stu-id="98b36-107">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="98b36-108">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="98b36-108">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="98b36-109">Bir XPath sorgusunda ad alanlarını kullanmak için, sınıfı gibi arabiriminden türetilmiş bir nesne, <xref:System.Xml.IXmlNamespaceResolver> <xref:System.Xml.XmlNamespaceManager> ad alanı URI 'Si ve XPath sorgusuna dahil edilecek ön ek ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="98b36-109">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="98b36-110"><xref:System.Xml.XmlNamespaceManager>Nesnesi, aşağıdaki yolların her birinde sorgusunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98b36-110">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="98b36-111"><xref:System.Xml.XmlNamespaceManager>Nesnesi, <xref:System.Xml.XPath.XPathExpression> nesnesinin yöntemi kullanılarak varolan bir nesneyle ilişkilendirilir <xref:System.Xml.XPath.XPathExpression.SetContext%2A> <xref:System.Xml.XPath.XPathExpression> .</span><span class="sxs-lookup"><span data-stu-id="98b36-111">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="98b36-112">Ayrıca, <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> XPath ifadesini ve bir nesneyi parametreler olarak temsil eden bir dize alan <xref:System.Xml.XmlNamespaceManager> ve yeni bir nesne döndüren static yöntemi kullanarak yeni bir nesne derleyebilirsiniz <xref:System.Xml.XPath.XPathExpression> .</span><span class="sxs-lookup"><span data-stu-id="98b36-112">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="98b36-113"><xref:System.Xml.XmlNamespaceManager>Nesnenin kendisi, <xref:System.Xml.XPath.XPathNavigator> XPath ifadesini temsil eden bir dize ile birlikte kabul eden bir sınıf yöntemine parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="98b36-113">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="98b36-114">Aşağıda, <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.IXmlNamespaceResolver> arabiriminden bir parametre olarak türetilmiş bir nesneyi kabul eden sınıfının yöntemleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="98b36-114">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="98b36-115">Varsayılan ad alanı</span><span class="sxs-lookup"><span data-stu-id="98b36-115">The Default Namespace</span></span>  
 <span data-ttu-id="98b36-116">Aşağıdaki XML belgesinde, ad alanını bildirmek için boş ön eki olan varsayılan ad alanı kullanılır `http://www.contoso.com/books` .</span><span class="sxs-lookup"><span data-stu-id="98b36-116">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="98b36-117">XPath, boş öneki `null` ad alanı olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="98b36-117">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="98b36-118">Diğer bir deyişle, XPath sorgularında yalnızca ad alanlarına eşlenmiş önekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98b36-118">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="98b36-119">Bu, varsayılan ad alanı olsa bile bir XML belgesinde bir ad alanı üzerinde sorgu yapmak istiyorsanız, bunun için bir ön ek tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="98b36-119">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="98b36-120">Örneğin, yukarıdaki XML belgesi için bir ön ek tanımlamadan, XPath sorgusu `/books/book` herhangi bir sonuç döndürmez.</span><span class="sxs-lookup"><span data-stu-id="98b36-120">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="98b36-121">Bir önek, bir ad alanında olmayan bazı düğümlerle ve bazıları varsayılan bir ad alanında yer alan bir düğüm sorgulanırken belirsizlik oluşmasını engellemek için bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98b36-121">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="98b36-122">Aşağıdaki kod, varsayılan ad alanı için bir ön ek tanımlar ve `book` ad alanındaki tüm öğeleri seçer `http://www.contoso.com/books` .</span><span class="sxs-lookup"><span data-stu-id="98b36-122">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98b36-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98b36-123">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="98b36-124">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="98b36-124">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="98b36-125">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="98b36-125">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="98b36-126">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="98b36-126">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="98b36-127">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="98b36-127">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="98b36-128">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="98b36-128">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="98b36-129">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="98b36-129">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
