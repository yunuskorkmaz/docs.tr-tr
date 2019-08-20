---
title: Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591265"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="38855-102">Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (C#)</span><span class="sxs-lookup"><span data-stu-id="38855-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="38855-103">Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38855-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="38855-104">Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir.</span><span class="sxs-lookup"><span data-stu-id="38855-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="38855-105">Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="38855-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="38855-106">En iyi yaklaşım, bunu sizin için <xref:System.Xml.Linq.Extensions.Remove%2A> sağlayacak olan genişletme yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="38855-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="38855-107">Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="38855-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="38855-108">İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür.</span><span class="sxs-lookup"><span data-stu-id="38855-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="38855-109">Daha fazla bilgi için bkz. [karma bildirim kodu/zorunlu kod hataları (LINQ to XML)C#()](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="38855-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="38855-110">Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-110">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="38855-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="38855-111">Method</span></span>|<span data-ttu-id="38855-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38855-112">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-113">Bir <xref:System.Xml.Linq.XAttribute> öğesini üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-114">Alt düğümleri bir <xref:System.Xml.Linq.XContainer>öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-115">Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="38855-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-116">, Özniteliklerini <xref:System.Xml.Linq.XElement>kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-117">Değerini geçirirseniz `null` , özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-117">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-118">Değer ' i `null` geçirirseniz, alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-118">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-119">Bir <xref:System.Xml.Linq.XNode> öğesini üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="38855-120">Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-120">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="38855-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="38855-121">Example</span></span>

### <a name="description"></a><span data-ttu-id="38855-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38855-122">Description</span></span>

<span data-ttu-id="38855-123">Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="38855-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="38855-124">İlk olarak, tek bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-124">First, it removes a single element.</span></span> <span data-ttu-id="38855-125">İkincisi, bir öğe koleksiyonunu alır, bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işlecini kullanarak bunları çıkarır ve koleksiyonu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="38855-126">Son olarak, bir öğe koleksiyonunu alır ve <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemini kullanarak onları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38855-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="38855-127"><xref:System.Linq.Enumerable.ToList%2A> İşleci hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="38855-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="38855-128">Kod</span><span class="sxs-lookup"><span data-stu-id="38855-128">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
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
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="38855-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38855-129">Comments</span></span>

<span data-ttu-id="38855-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="38855-130">This code produces the following output:</span></span>

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

<span data-ttu-id="38855-131">İlk alt öğenin öğesinden `Child1`çıkarıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="38855-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="38855-132">Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından `Child3`kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="38855-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
