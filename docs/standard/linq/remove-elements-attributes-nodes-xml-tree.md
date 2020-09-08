---
title: XML ağacından öğe, öznitelik ve düğümleri kaldırma-LINQ to XML
description: Öğeleri, öznitelikleri ve diğer düğüm türlerini bir XML ağacından kaldırmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553889"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a><span data-ttu-id="f8ccb-103">XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f8ccb-103">Remove elements, attributes, and nodes from an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="f8ccb-104">Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-104">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="f8ccb-105">Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-105">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="f8ccb-106">Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-106">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="f8ccb-107">En iyi yaklaşım, <xref:System.Xml.Linq.Extensions.Remove%2A> bunu yapmak için genişletme yöntemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-107">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method to do this.</span></span>

<span data-ttu-id="f8ccb-108">Bu yaklaşımı kullanmanın başlıca nedeni, bir XML ağacından aldığınız koleksiyonların çoğu ertelenmiş yürütme kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-108">The main reason to use this approach is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="f8ccb-109">Önce bunları bir liste içine veya genişletme yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-109">If you don't first materialize them into a list, or if you don't use the extension methods, you may encounter a certain class of bugs.</span></span> <span data-ttu-id="f8ccb-110">Daha fazla bilgi için bkz. [karma bildirime dayalı/zorunlu kod hataları](mixed-declarative-imperative-code-bugs.md).</span><span class="sxs-lookup"><span data-stu-id="f8ccb-110">For more information, see [Mixed declarative/imperative code bugs](mixed-declarative-imperative-code-bugs.md).</span></span>

<span data-ttu-id="f8ccb-111">Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-111">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="f8ccb-112">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f8ccb-112">Method</span></span>|<span data-ttu-id="f8ccb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8ccb-113">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-114">Bir üst öğeden kaldırın <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-114">Remove an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-115">Alt düğümleri bir öğesinden kaldırın <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-115">Remove the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-116">İçinden içerik ve öznitelikleri kaldırın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-116">Remove content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-117">Özniteliklerini kaldırın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-117">Remove the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-118">Değeri geçirirseniz özniteliği kaldırın `null` .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-118">Remove the attribute if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-119">Değeri geçirirseniz alt öğesi kaldırın `null` .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-119">Remove the child element if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-120">Bir üst öğeden kaldırın <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-120">Remove an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f8ccb-121">Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-121">Remove every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a><span data-ttu-id="f8ccb-122">Örnek: tek bir öğeyi kaldırın ve iki şekilde bir öğe koleksiyonunu kaldırın</span><span class="sxs-lookup"><span data-stu-id="f8ccb-122">Example: Remove a single element, and remove a collection of elements in two ways</span></span>

<span data-ttu-id="f8ccb-123">Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="f8ccb-124">İlk olarak, tek bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-124">First, it removes a single element.</span></span> <span data-ttu-id="f8ccb-125">İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve sonra koleksiyonu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8ccb-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and then removes the collection.</span></span> <span data-ttu-id="f8ccb-126">Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="f8ccb-127">İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) ve [veri türlerini dönüştürme (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8ccb-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) and [Converting Data Types (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>

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

<span data-ttu-id="f8ccb-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f8ccb-128">This example produces the following output:</span></span>

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

<span data-ttu-id="f8ccb-129">İlk alt öğe öğesinden kaldırılmıştır `Child1` ve tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .</span><span class="sxs-lookup"><span data-stu-id="f8ccb-129">The first grandchild element was removed from `Child1`, and all grandchildren elements were removed from `Child2` and from `Child3`.</span></span>
