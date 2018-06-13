---
title: XML verileri XPathNavigator kullanarak seçin
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c937754f031420d90f89bf89563db17ddaaf3bbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572128"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="7ee6c-102">XML verileri XPathNavigator kullanarak seçin</span><span class="sxs-lookup"><span data-stu-id="7ee6c-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="7ee6c-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümler kümesi seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="7ee6c-104">Seçildiğinde, seçilen düğümler küme üzerinde yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="7ee6c-105">XPathNavigator seçimi yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7ee6c-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="7ee6c-106"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümler kümesi seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="7ee6c-107"><xref:System.Xml.XPath.XPathNavigator> Sınıfı ayrıca bir XPath ifadesi kullanarak daha hızlı üst, alt ve alt düğümlerini seçmek için en iyi duruma getirilmiş yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="7ee6c-108">Seçili düğüm kümesi döndürülür bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> tek Seçili düğümün söz konusu olduğunda nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="7ee6c-109">XPath ifadeler kullanarak düğümleri seçme</span><span class="sxs-lookup"><span data-stu-id="7ee6c-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="7ee6c-110">Bir XPath ifadesi kullanarak düğümleri kümesi seçmek için aşağıdaki seçimi yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="7ee6c-111">Çağrıldığında, bu yöntemleri serbestçe kullanarak gezinme düğümleri kümesi döndürür. bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> tek Seçili düğümün söz konusu olduğunda nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="7ee6c-112">Gezinme bir <xref:System.Xml.XPath.XPathNodeIterator> nesne konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="7ee6c-113"><xref:System.Xml.XPath.XPathNavigator> Döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemleri tek döndürülen düğümde yerleştirilir ve ayrıca konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="7ee6c-114">Aşağıdaki örnek oluşturulmasını gösterir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.Xml.XPath.XPathDocument> nesnesi, kullanımını <xref:System.Xml.XPath.XPathNavigator.Select%2A> düğümler seçmek için yöntemi <xref:System.Xml.XPath.XPathDocument> nesne ve kullanımını <xref:System.Xml.XPath.XPathNodeIterator> seçili düğümler yineleme için nesne.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="7ee6c-115">Örnek alır `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="7ee6c-116">En iyi duruma getirilmiş seçimi yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7ee6c-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="7ee6c-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı alt, alt ve üst düğümleri almak için yaygın olarak kullanılan XPath ifadeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="7ee6c-118">Bu yöntemler için performansı en iyi duruma getirilir ve bunların karşılık gelen XPath ifadeleri hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="7ee6c-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri seçer üst, alt ve alt düğümler dayalı bir <xref:System.Xml.XPath.XPathNodeType> değeri veya yerel ad ve ad alanı seçmek için düğümlerin URI.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="7ee6c-120">Seçilen üst, alt ve alt düğümler döndürülür bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee6c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ee6c-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="7ee6c-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="7ee6c-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="7ee6c-123">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7ee6c-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="7ee6c-124">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="7ee6c-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="7ee6c-125">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="7ee6c-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="7ee6c-126">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="7ee6c-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="7ee6c-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7ee6c-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
