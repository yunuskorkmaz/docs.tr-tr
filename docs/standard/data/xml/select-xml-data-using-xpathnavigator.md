---
title: XPathNavigator Kullanarak XML Verileri Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710173"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="45d04-102">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="45d04-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="45d04-103"><xref:System.Xml.XPath.XPathNavigator> sınıfı bir XPath ifadesi kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğüm kümesini seçmek için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="45d04-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="45d04-104">Seçili düğüm kümesi üzerinde yineleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45d04-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="45d04-105">XPathNavigator seçim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="45d04-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="45d04-106"><xref:System.Xml.XPath.XPathNavigator> sınıfı bir XPath ifadesi kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğüm kümesini seçmek için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="45d04-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="45d04-107"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XPath ifadesi kullanmaktan daha hızlı üst, alt ve alt düğümleri seçmek için iyileştirilmiş bir yöntemler kümesi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="45d04-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="45d04-108">Seçili düğüm kümesi, tek bir seçili düğüm olması durumunda <xref:System.Xml.XPath.XPathNodeIterator> nesne veya bir <xref:System.Xml.XPath.XPathNavigator> nesnesi içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="45d04-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="45d04-109">XPath Ifadeleri kullanarak düğüm seçme</span><span class="sxs-lookup"><span data-stu-id="45d04-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="45d04-110">Bir XPath ifadesi kullanarak bir düğüm kümesi seçmek için aşağıdaki seçim yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d04-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="45d04-111">Çağrıldığında, bu yöntemler bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya tek bir seçili düğüm olması durumunda <xref:System.Xml.XPath.XPathNavigator> bir nesne kullanarak serbestçe gezinebileceğiniz bir düğüm kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45d04-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="45d04-112">Bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesiyle gezinmek, onu oluşturmak için kullanılan <xref:System.Xml.XPath.XPathNavigator> nesnesinin konumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="45d04-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="45d04-113"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metotlarından döndürülen <xref:System.Xml.XPath.XPathNavigator> nesnesi, tek döndürülen düğümde konumlandırılır ve ayrıca onu oluşturmak için kullanılan <xref:System.Xml.XPath.XPathNavigator> nesnesinin konumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="45d04-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="45d04-114">Aşağıdaki örnek, bir <xref:System.Xml.XPath.XPathDocument> nesnesinden <xref:System.Xml.XPath.XPathNavigator> nesnesinin oluşturulmasını, <xref:System.Xml.XPath.XPathDocument> nesnesindeki düğümleri seçmek için <xref:System.Xml.XPath.XPathNavigator.Select%2A> yönteminin kullanımını ve seçilen düğümlerin üzerinde yinelemek için <xref:System.Xml.XPath.XPathNodeIterator> nesnesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45d04-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="45d04-115">Örnek, `books.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="45d04-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="45d04-116">İyileştirilmiş seçim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="45d04-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="45d04-117"><xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri, genel, alt ve üst düğümleri almak için yaygın olarak kullanılan XPath ifadelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="45d04-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="45d04-118">Bu yöntemler performans için iyileştirilmiştir ve bunlara karşılık gelen XPath ifadelerinden daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="45d04-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="45d04-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri, bir <xref:System.Xml.XPath.XPathNodeType> değere veya seçilecek düğümlerin yerel adına ve ad alanı URI 'sine göre üst, alt ve alt düğümleri seçer.</span><span class="sxs-lookup"><span data-stu-id="45d04-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="45d04-120">Seçilen üst öğe, alt ve alt düğümler bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="45d04-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d04-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45d04-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="45d04-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="45d04-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="45d04-123">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="45d04-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="45d04-124">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="45d04-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="45d04-125">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="45d04-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="45d04-126">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="45d04-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="45d04-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="45d04-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
