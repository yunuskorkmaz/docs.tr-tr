---
title: XML Ağacından Öğe, Öznitelik ve Düğümleri Kaldırma
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413419"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="7ae01-102">Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ae01-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="7ae01-103">Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ae01-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="7ae01-104">Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir.</span><span class="sxs-lookup"><span data-stu-id="7ae01-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="7ae01-105">Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7ae01-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="7ae01-106">En iyi yaklaşım, bunu <xref:System.Xml.Linq.Extensions.Remove%2A> sizin için sağlayacak olan genişletme yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="7ae01-107">Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="7ae01-108">İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7ae01-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="7ae01-109">Daha fazla bilgi için bkz. [karma bildirim kodu/tanımlayıcı kod hataları (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7ae01-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7ae01-110">Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="7ae01-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ae01-111">Method</span></span>|<span data-ttu-id="7ae01-112">Description</span><span class="sxs-lookup"><span data-stu-id="7ae01-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-113">Bir öğesini <xref:System.Xml.Linq.XAttribute> üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-114">Alt düğümleri bir öğesinden kaldırır <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="7ae01-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-115">Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="7ae01-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-116">, Özniteliklerini kaldırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="7ae01-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-117">`null`Değerini geçirirseniz, özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-118">`null`Değer ' i geçirirseniz, alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-119">Bir öğesini <xref:System.Xml.Linq.XNode> üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7ae01-120">Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7ae01-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ae01-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7ae01-122">Description</span><span class="sxs-lookup"><span data-stu-id="7ae01-122">Description</span></span>  
 <span data-ttu-id="7ae01-123">Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ae01-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="7ae01-124">İlk olarak, tek bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-124">First, it removes a single element.</span></span> <span data-ttu-id="7ae01-125">İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve koleksiyonu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ae01-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="7ae01-126">Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .</span><span class="sxs-lookup"><span data-stu-id="7ae01-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="7ae01-127">İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (Visual Basic)](converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ae01-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="7ae01-128">Kod</span><span class="sxs-lookup"><span data-stu-id="7ae01-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="7ae01-129">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="7ae01-129">Comments</span></span>  
 <span data-ttu-id="7ae01-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7ae01-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="7ae01-131">İlk alt öğenin öğesinden çıkarıldığına dikkat edin `Child1` .</span><span class="sxs-lookup"><span data-stu-id="7ae01-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="7ae01-132">Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .</span><span class="sxs-lookup"><span data-stu-id="7ae01-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae01-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae01-133">See also</span></span>

- [<span data-ttu-id="7ae01-134">XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ae01-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
