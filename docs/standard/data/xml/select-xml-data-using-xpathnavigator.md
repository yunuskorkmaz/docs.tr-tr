---
title: XPathNavigator Kullanarak XML Verileri Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d5e7074fc8c68a0a0243ea4ad237e713e0a729b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289063"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="56bfc-102">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="56bfc-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="56bfc-103">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> XPath ifadesi kullanarak bir veya nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="56bfc-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="56bfc-104">Seçili düğüm kümesi üzerinde yineleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bfc-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="56bfc-105">XPathNavigator seçim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="56bfc-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="56bfc-106">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> XPath ifadesi kullanarak bir veya nesnesindeki düğüm kümesi seçmek için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="56bfc-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="56bfc-107"><xref:System.Xml.XPath.XPathNavigator>Sınıfı ayrıca, bir XPath ifadesi kullanmaktan daha hızlı üst, alt ve alt düğümleri seçmek için iyileştirilmiş bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56bfc-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="56bfc-108">Seçili düğüm kümesi, <xref:System.Xml.XPath.XPathNodeIterator> <xref:System.Xml.XPath.XPathNavigator> tek bir seçili düğüm olması durumunda bir nesne veya nesne içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="56bfc-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="56bfc-109">XPath Ifadeleri kullanarak düğüm seçme</span><span class="sxs-lookup"><span data-stu-id="56bfc-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="56bfc-110">Bir XPath ifadesi kullanarak bir düğüm kümesi seçmek için aşağıdaki seçim yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56bfc-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="56bfc-111">Çağrıldığında, bu yöntemler bir <xref:System.Xml.XPath.XPathNodeIterator> nesne veya <xref:System.Xml.XPath.XPathNavigator> tek bir seçili düğüm durumunda bir nesne kullanarak serbestçe gezinebileceğiniz bir düğüm kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="56bfc-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="56bfc-112">Bir nesneyle gezinmek, <xref:System.Xml.XPath.XPathNodeIterator> <xref:System.Xml.XPath.XPathNavigator> onu oluşturmak için kullanılan nesnenin konumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="56bfc-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="56bfc-113"><xref:System.Xml.XPath.XPathNavigator>Metotlardan döndürülen nesne, <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> tek döndürülen düğümde konumlandırılır ve ayrıca <xref:System.Xml.XPath.XPathNavigator> onu oluşturmak için kullanılan nesnenin konumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="56bfc-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="56bfc-114">Aşağıdaki örnek, bir nesneden bir nesnenin oluşturulmasını <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> , <xref:System.Xml.XPath.XPathNavigator.Select%2A> nesne içindeki düğümleri seçmek için yönteminin kullanımını <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XPath.XPathNodeIterator> seçilen düğümlerin üzerinde yinelemek için nesnesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="56bfc-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="56bfc-115">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="56bfc-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="56bfc-116">İyileştirilmiş seçim yöntemleri</span><span class="sxs-lookup"><span data-stu-id="56bfc-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="56bfc-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri, <xref:System.Xml.XPath.XPathNavigator> Genel, alt ve üst düğümleri almak Için yaygın olarak kullanılan XPath ifadelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="56bfc-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="56bfc-118">Bu yöntemler performans için iyileştirilmiştir ve bunlara karşılık gelen XPath ifadelerinden daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="56bfc-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="56bfc-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri bir <xref:System.Xml.XPath.XPathNodeType> değere veya seçilecek düğümlerin yerel adına ve ad alanı URI 'sine göre üst, alt ve alt düğümleri seçer.</span><span class="sxs-lookup"><span data-stu-id="56bfc-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="56bfc-120">Seçili üst öğe, alt ve alt düğümleri bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="56bfc-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bfc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56bfc-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="56bfc-122">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="56bfc-122">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="56bfc-123">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="56bfc-123">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="56bfc-124">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="56bfc-124">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="56bfc-125">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="56bfc-125">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="56bfc-126">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="56bfc-126">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="56bfc-127">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="56bfc-127">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
