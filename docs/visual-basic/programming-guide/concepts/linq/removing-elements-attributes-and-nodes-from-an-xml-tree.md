---
title: (Visual Basic) XML ağacından öğe, öznitelik ve düğümleri kaldırma
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 85a7a3b4047e269c562177cfa045b952472aaac2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814919"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="3504f-102">(Visual Basic) XML ağacından öğe, öznitelik ve düğümleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="3504f-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="3504f-103">Bir XML ağacına öğe, öznitelik ve düğümleri diğer türleri kaldırma değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3504f-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="3504f-104">Tek bir öğe veya tek bir öznitelik, bir XML belgesinden kaldırma açıktır.</span><span class="sxs-lookup"><span data-stu-id="3504f-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="3504f-105">Ancak, öğeler veya öznitelikleri koleksiyonları kaldırırken, ilk listesini bir koleksiyona depolanabildiği ve öğeler veya öznitelikleri listeden silin.</span><span class="sxs-lookup"><span data-stu-id="3504f-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="3504f-106">En iyi yaklaşımdır <xref:System.Xml.Linq.Extensions.Remove%2A> bu sizin için yapacak genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3504f-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="3504f-107">Bunu yapmak için ana nedeni, bir XML ağacından almak koleksiyonların çoğu ertelenmiş yürütme kullanarak veriyor, olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3504f-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="3504f-108">Önce bunları bir liste olarak depolanabildiği değil veya uzantı yöntemlerini kullanmazsanız, belirli bir sınıf hataların karşılaşmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3504f-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="3504f-109">Daha fazla bilgi için [karma bildirim temelli kod/kesinliği kod hataları karışımı (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3504f-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3504f-110">Aşağıdaki yöntemlerden bir XML ağacından düğümleri ve özniteliklerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3504f-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="3504f-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3504f-111">Method</span></span>|<span data-ttu-id="3504f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3504f-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-113">Kaldırır bir <xref:System.Xml.Linq.XAttribute> üst öğesinden.</span><span class="sxs-lookup"><span data-stu-id="3504f-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-114">Alt düğümleri kaldırır bir <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="3504f-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-115">İçerik kaldırır ve özniteliklerini bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3504f-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-116">Özniteliklerini kaldırır bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3504f-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-117">Geçirirseniz `null` değeri için ardından özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3504f-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-118">Geçirirseniz `null` değeri için ardından alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3504f-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-119">Kaldırır bir <xref:System.Xml.Linq.XNode> üst öğesinden.</span><span class="sxs-lookup"><span data-stu-id="3504f-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="3504f-120">Her bir öznitelik veya öğenin üst öğesi kaynak koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3504f-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3504f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3504f-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3504f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3504f-122">Description</span></span>  
 <span data-ttu-id="3504f-123">Bu örnekte, öğelerin kaldırılması için üç yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3504f-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="3504f-124">İlk olarak, tek bir öğe kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3504f-124">First, it removes a single element.</span></span> <span data-ttu-id="3504f-125">İkinci olarak, öğelerinin bir koleksiyonunu alır, bunları gerçekleştiren kullanarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işleci ve koleksiyon kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3504f-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="3504f-126">Son olarak, öğelerinin bir koleksiyonunu alır ve bunları kaldırır kullanarak <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3504f-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="3504f-127">Daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> işleci bkz [dönüştürme veri türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3504f-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="3504f-128">Kod</span><span class="sxs-lookup"><span data-stu-id="3504f-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="3504f-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3504f-129">Comments</span></span>  
 <span data-ttu-id="3504f-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3504f-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="3504f-131">İlk en alt öğeyi kaldırılmıştır bildirimi `Child1`.</span><span class="sxs-lookup"><span data-stu-id="3504f-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="3504f-132">Tüm alt bağımlı öğelere öğeleri kaldırılmış olan `Child2` ve `Child3`.</span><span class="sxs-lookup"><span data-stu-id="3504f-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3504f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3504f-133">See also</span></span>

- [<span data-ttu-id="3504f-134">(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3504f-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
