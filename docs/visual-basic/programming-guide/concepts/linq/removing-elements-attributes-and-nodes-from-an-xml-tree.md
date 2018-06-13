---
title: Öğeleri, öznitelikleri ve düğümler XML ağacından (Visual Basic) kaldırılıyor
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: dbc5cfd7bf6e1f1b77dd14a6771c387fac29d062
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645936"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="16cd0-102">Öğeleri, öznitelikleri ve düğümler XML ağacından (Visual Basic) kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="16cd0-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="16cd0-103">Bir XML ağacı öğeleri, öznitelikleri ve diğer tür düğüm kaldırma değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16cd0-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="16cd0-104">Tek bir öğe veya tek bir öznitelik bir XML belgesinden kaldırma basittir.</span><span class="sxs-lookup"><span data-stu-id="16cd0-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="16cd0-105">Ancak, koleksiyonları öğelerin veya özniteliklerin kaldırırken, ilk listesini koleksiyona gerçekleştirmeye ve gerekir öznitelikler ve öğeler listeden silin.</span><span class="sxs-lookup"><span data-stu-id="16cd0-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="16cd0-106">Kullanmak için en iyi yaklaşımdır <xref:System.Xml.Linq.Extensions.Remove%2A> bu sizin için yapar genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16cd0-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="16cd0-107">Bunu yapmak için ana nedeni, bir XML ağacından almak koleksiyonları çoğunu kullanılarak ertelenmiş yürütme verdiğini olduğunu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="16cd0-108">İlk önce bunları bir liste olarak gerçekleştirmeye değil ya da uzantı yöntemleri kullanmazsanız, belirli bir sınıf hataların karşılaştığınız mümkündür.</span><span class="sxs-lookup"><span data-stu-id="16cd0-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="16cd0-109">Daha fazla bilgi için bkz: [karma bildirim temelli kod/kesinliği kod hataları (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16cd0-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="16cd0-110">Aşağıdaki yöntemlerden bir XML ağacından düğümleri ve öznitelikleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="16cd0-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="16cd0-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="16cd0-111">Method</span></span>|<span data-ttu-id="16cd0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16cd0-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-113">Kaldırır bir <xref:System.Xml.Linq.XAttribute> kendi üst öğesinden.</span><span class="sxs-lookup"><span data-stu-id="16cd0-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-114">Alt düğümleri kaldırır bir <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="16cd0-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-115">İçerik kaldırır ve özniteliklerini bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="16cd0-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-116">Özniteliklerini kaldırır bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="16cd0-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-117">Geçirirseniz `null` öznitelik için değer, ardından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-118">Geçirirseniz `null` için değer, sonra alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-119">Kaldırır bir <xref:System.Xml.Linq.XNode> kendi üst öğesinden.</span><span class="sxs-lookup"><span data-stu-id="16cd0-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="16cd0-120">Her öznitelik veya öğenin üst öğesi kaynak koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16cd0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="16cd0-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="16cd0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16cd0-122">Description</span></span>  
 <span data-ttu-id="16cd0-123">Bu örnek, öğe kaldırma için üç yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cd0-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="16cd0-124">İlk olarak, tek bir öğe kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-124">First, it removes a single element.</span></span> <span data-ttu-id="16cd0-125">İkinci olarak, öğe koleksiyonunu alır, bunları gerçeğe kullanarak <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işleci ve koleksiyon kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16cd0-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="16cd0-126">Son olarak, öğe koleksiyonunu alır ve bunları kaldırır kullanarak <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16cd0-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="16cd0-127">Daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> işleci, bkz: [dönüştürme veri türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="16cd0-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="16cd0-128">Kod</span><span class="sxs-lookup"><span data-stu-id="16cd0-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="16cd0-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16cd0-129">Comments</span></span>  
 <span data-ttu-id="16cd0-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="16cd0-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="16cd0-131">İlk en alt öğe kaldırıldığı bildirimi `Child1`.</span><span class="sxs-lookup"><span data-stu-id="16cd0-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="16cd0-132">Tüm alt bağımlı öğelere öğeleri kaldırılmış olan `Child2` ve `Child3`.</span><span class="sxs-lookup"><span data-stu-id="16cd0-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cd0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16cd0-133">See Also</span></span>  
 [<span data-ttu-id="16cd0-134">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16cd0-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
