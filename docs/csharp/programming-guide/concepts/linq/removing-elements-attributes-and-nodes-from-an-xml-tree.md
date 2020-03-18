---
title: XML Ağacından Öğeleri, Öznitelikleri ve Düğümleri Kaldırma (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591265"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="c59ec-102">XML Ağacından Öğeleri, Öznitelikleri ve Düğümleri Kaldırma (C#)</span><span class="sxs-lookup"><span data-stu-id="c59ec-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="c59ec-103">Öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırarak bir XML ağacını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c59ec-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="c59ec-104">Bir XML belgesinden tek bir öğeyi veya tek bir özniteliği kaldırmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="c59ec-105">Ancak, öğe veya öznitelik koleksiyonlarını kaldırırken, önce bir koleksiyonu bir listeye eklemeniz ve ardından öğeleri veya öznitelikleri listeden silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c59ec-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="c59ec-106">En iyi yaklaşım, <xref:System.Xml.Linq.Extensions.Remove%2A> bunu sizin için yapacak uzantı yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="c59ec-107">Bunu yapmanın temel nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak elde edilmesidir.</span><span class="sxs-lookup"><span data-stu-id="c59ec-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="c59ec-108">Bunları ilk önce bir listeye dahil etmezseniz veya uzantı yöntemlerini kullanmazsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c59ec-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="c59ec-109">Daha fazla bilgi için bkz: [Karışık Bildirim kodu/Zorunlu Kod Hataları (LINQ - XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c59ec-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="c59ec-110">Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-110">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="c59ec-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c59ec-111">Method</span></span>|<span data-ttu-id="c59ec-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59ec-112">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-113">Bir ebeveynini <xref:System.Xml.Linq.XAttribute> kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-114">Alt düğümleri bir <xref:System.Xml.Linq.XContainer>'den kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-115">İçeriği ve öznitelikleri <xref:System.Xml.Linq.XElement>bir 'den kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-116">Bir <xref:System.Xml.Linq.XElement>' nin özniteliklerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-117">Değer için `null` geçerseniz, özniteliği kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-117">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-118">Değer için `null` geçerseniz, alt öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-118">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-119">Bir ebeveynini <xref:System.Xml.Linq.XNode> kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c59ec-120">Kaynak koleksiyonundaki her özniteliği veya öğeyi üst öğeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-120">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="c59ec-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c59ec-121">Example</span></span>

### <a name="description"></a><span data-ttu-id="c59ec-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59ec-122">Description</span></span>

<span data-ttu-id="c59ec-123">Bu örnek, öğeleri kaldırmak için üç yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="c59ec-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="c59ec-124">İlk olarak, tek bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-124">First, it removes a single element.</span></span> <span data-ttu-id="c59ec-125">İkinci olarak, bir öğe koleksiyonunu alır, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işleci kullanarak bunları somutlaştırır ve koleksiyonu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="c59ec-126">Son olarak, bir öğe koleksiyonu alır ve <xref:System.Xml.Linq.Extensions.Remove%2A> uzantı yöntemini kullanarak bunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c59ec-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="c59ec-127"><xref:System.Linq.Enumerable.ToList%2A> İşleç hakkında daha fazla bilgi için [bkz.](./converting-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c59ec-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="c59ec-128">Kod</span><span class="sxs-lookup"><span data-stu-id="c59ec-128">Code</span></span>

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

### <a name="comments"></a><span data-ttu-id="c59ec-129">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="c59ec-129">Comments</span></span>

<span data-ttu-id="c59ec-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c59ec-130">This code produces the following output:</span></span>

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

<span data-ttu-id="c59ec-131">İlk torun öğesinin `Child1`.</span><span class="sxs-lookup"><span data-stu-id="c59ec-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="c59ec-132">Tüm torun elemanları `Child2` kaldırıldı `Child3`ve .</span><span class="sxs-lookup"><span data-stu-id="c59ec-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
