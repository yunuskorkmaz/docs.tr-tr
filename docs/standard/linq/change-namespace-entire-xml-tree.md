---
title: Tüm XML ağacının ad alanını değiştirme-LINQ to XML
description: Tüm XML ağacının ad alanını değiştirme hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: ac4eda71dd536ed2f940f1e86a0190ef337c386a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553397"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-linq-to-xml"></a><span data-ttu-id="220e6-103">Tüm XML ağacının ad alanını değiştirme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="220e6-103">How to change the namespace for an entire XML tree (LINQ to XML)</span></span>

<span data-ttu-id="220e6-104">Bazen bir öğe veya öznitelik için ad alanını programlı olarak değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="220e6-104">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="220e6-105">LINQ to XML bu kadar kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="220e6-105">LINQ to XML makes this easy.</span></span> <span data-ttu-id="220e6-106"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType>Özelliği ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="220e6-106">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="220e6-107"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>Özelliği ayarlanamaz, ancak öznitelikleri bir öğesine kolayca kopyalayabilir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , var olan öznitelikleri kaldırabilir ve ardından yeni istenen ad alanındaki yeni öznitelikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="220e6-107">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property can't be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>

<span data-ttu-id="220e6-108">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="220e6-108">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-create-two-xml-trees-change-the-namespaces-and-combine-the-trees"></a><span data-ttu-id="220e6-109">Örnek: iki XML ağacı oluşturma, ad alanlarını değiştirme ve ağaçları birleştirme</span><span class="sxs-lookup"><span data-stu-id="220e6-109">Example: Create two XML trees, change the namespaces, and combine the trees</span></span>

<span data-ttu-id="220e6-110">Aşağıdaki kod, ad alanı olmadan iki XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="220e6-110">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="220e6-111">Daha sonra ağaçların her birinin ad alanını değiştirir ve bunları tek bir ağaçta birleştirir.</span><span class="sxs-lookup"><span data-stu-id="220e6-111">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>

```csharp
XElement tree1 = new XElement("Data",
    new XElement("Child", "content",
        new XAttribute("MyAttr", "content")
    )
);
XElement tree2 = new XElement("Data",
    new XElement("Child", "content",
        new XAttribute("MyAttr", "content")
    )
);
XNamespace aw = "http://www.adventure-works.com";
XNamespace ad = "http://www.adatum.com";
// Change the namespace of every element and attribute in the first tree.
foreach (XElement el in tree1.DescendantsAndSelf())
{
    el.Name = aw.GetName(el.Name.LocalName);
    List<XAttribute> atList = el.Attributes().ToList();
    el.Attributes().Remove();
    foreach (XAttribute at in atList)
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));
}
// Change the namespace of every element and attribute in the second tree.
foreach (XElement el in tree2.DescendantsAndSelf())
{
    el.Name = ad.GetName(el.Name.LocalName);
    List<XAttribute> atList = el.Attributes().ToList();
    el.Attributes().Remove();
    foreach (XAttribute at in atList)
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));
}
// Add attribute namespaces so that the tree will be serialized with
// the aw and ad namespace prefixes.
tree1.Add(
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")
);
tree2.Add(
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")
);
// Create a new composite tree.
XElement root = new XElement("Root",
    tree1,
    tree2
);
Console.WriteLine(root);
```

```vb
Dim tree1 As XElement = _
    <Data>
        <Child MyAttr="content">content</Child>
    </Data>
Dim tree2 As XElement = _
    <Data>
        <Child MyAttr="content">content</Child>
    </Data>
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim ad As XNamespace = "http://www.adatum.com"
' Change the namespace of every element and attribute in the first tree.
For Each el As XElement In tree1.DescendantsAndSelf
    el.Name = aw.GetName(el.Name.LocalName)
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()
    el.Attributes().Remove()
    For Each at As XAttribute In atList
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))
    Next
Next
' Change the namespace of every element and attribute in the second tree.
For Each el As XElement In tree2.DescendantsAndSelf()
    el.Name = ad.GetName(el.Name.LocalName)
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()
    el.Attributes().Remove()
    For Each at As XAttribute In atList
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))
    Next
Next
' Add attribute namespaces so that the tree will be serialized with
' the aw and ad namespace prefixes.
tree1.Add( _
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _
)
tree2.Add( _
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _
)
' Create a new composite tree.
Dim root As XElement = _
    <Root>
        <%= tree1 %>
        <%= tree2 %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="220e6-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="220e6-112">This example produces the following output:</span></span>

```xml
<Root>
  <aw:Data xmlns:aw="http://www.adventure-works.com">
    <aw:Child aw:MyAttr="content">content</aw:Child>
  </aw:Data>
  <ad:Data xmlns:ad="http://www.adatum.com">
    <ad:Child ad:MyAttr="content">content</ad:Child>
  </ad:Data>
</Root>
```
