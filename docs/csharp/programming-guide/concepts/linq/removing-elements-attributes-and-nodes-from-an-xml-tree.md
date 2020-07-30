---
title: XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (C#)
description: Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırmayı öğrenin. Kaldırma yöntemlerinin listesini ve kod örneğini görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300052"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="00f7d-104">XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (C#)</span><span class="sxs-lookup"><span data-stu-id="00f7d-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="00f7d-105">Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00f7d-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="00f7d-106">Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir.</span><span class="sxs-lookup"><span data-stu-id="00f7d-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="00f7d-107">Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="00f7d-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="00f7d-108">En iyi yaklaşım, bunu <xref:System.Xml.Linq.Extensions.Remove%2A> sizin için sağlayacak olan genişletme yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="00f7d-109">Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="00f7d-110">İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür.</span><span class="sxs-lookup"><span data-stu-id="00f7d-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="00f7d-111">Daha fazla bilgi için bkz. [karma bildirim kodu/zorunlu kod hataları (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="00f7d-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="00f7d-112">Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="00f7d-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="00f7d-113">Method</span></span>|<span data-ttu-id="00f7d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00f7d-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-115">Bir öğesini <xref:System.Xml.Linq.XAttribute> üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-116">Alt düğümleri bir öğesinden kaldırır <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="00f7d-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-117">Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="00f7d-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-118">, Özniteliklerini kaldırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="00f7d-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-119">`null`Değerini geçirirseniz, özniteliğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-120">`null`Değer ' i geçirirseniz, alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-121">Bir öğesini <xref:System.Xml.Linq.XNode> üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="00f7d-122">Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="00f7d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="00f7d-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="00f7d-124">Description</span><span class="sxs-lookup"><span data-stu-id="00f7d-124">Description</span></span>

<span data-ttu-id="00f7d-125">Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="00f7d-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="00f7d-126">İlk olarak, tek bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-126">First, it removes a single element.</span></span> <span data-ttu-id="00f7d-127">İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve koleksiyonu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="00f7d-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="00f7d-128">Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .</span><span class="sxs-lookup"><span data-stu-id="00f7d-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="00f7d-129">İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="00f7d-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="00f7d-130">Kod</span><span class="sxs-lookup"><span data-stu-id="00f7d-130">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="00f7d-131">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="00f7d-131">Comments</span></span>

<span data-ttu-id="00f7d-132">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="00f7d-132">This code produces the following output:</span></span>

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

<span data-ttu-id="00f7d-133">İlk alt öğenin öğesinden çıkarıldığına dikkat edin `Child1` .</span><span class="sxs-lookup"><span data-stu-id="00f7d-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="00f7d-134">Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .</span><span class="sxs-lookup"><span data-stu-id="00f7d-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
