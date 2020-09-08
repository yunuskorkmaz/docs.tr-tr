---
title: Alt öğeler yöntemini kullanarak tek bir alt öğe bulma-LINQ to XML
description: Tek bir benzersiz adlı alt öğe bulmak için XContainer. Bağımlıı eksenini kullanın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 9065309822bfb7c46da556fcf9b3a3b48df16302
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553154"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-linq-to-xml"></a><span data-ttu-id="cdc1f-103">Alt öğeler yöntemini kullanarak tek bir alt öğe bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cdc1f-103">How to find a single descendant using the Descendants method (LINQ to XML)</span></span>

<span data-ttu-id="cdc1f-104"><xref:System.Xml.Linq.XContainer.Descendants%2A>Tek bir benzersiz adlı alt öğe bulmak için Axis yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc1f-104">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely-named descendant element.</span></span> <span data-ttu-id="cdc1f-105">Bu teknik özellikle belirli bir ada sahip belirli bir alt öğe bulmak istediğinizde yararlıdır ve XML ağacında gezinilirken daha hızlı ve kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc1f-105">This technique is especially useful when you want to find a particular descendant with a specific name, and may be faster and easier to use than navigating the XML tree.</span></span>

## <a name="example-use-xcontainerdescendants-to-find-a-single-uniquely-named-descendant-element"></a><span data-ttu-id="cdc1f-106">Örnek: tek bir benzersiz adlı alt öğe bulmak için XContainer. bağımlıları kullanın</span><span class="sxs-lookup"><span data-stu-id="cdc1f-106">Example: Use XContainer.Descendants to find a single uniquely-named descendant element</span></span>

<span data-ttu-id="cdc1f-107">Bu örnek, <xref:System.Linq.Enumerable.First%2A> Standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cdc1f-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <GrandChild1>GC1 Value</GrandChild1>
  </Child1>
  <Child2>
    <GrandChild2>GC2 Value</GrandChild2>
  </Child2>
  <Child3>
    <GrandChild3>GC3 Value</GrandChild3>
  </Child3>
  <Child4>
    <GrandChild4>GC4 Value</GrandChild4>
  </Child4>
</Root>");
string grandChild3 = (string)
    (from el in root.Descendants("GrandChild3")
    select el).First();
Console.WriteLine(grandChild3);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1>GC1 Value</GrandChild1>
        </Child1>
        <Child2>
            <GrandChild2>GC2 Value</GrandChild2>
        </Child2>
        <Child3>
            <GrandChild3>GC3 Value</GrandChild3>
        </Child3>
        <Child4>
            <GrandChild4>GC4 Value</GrandChild4>
        </Child4>
    </Root>
Dim grandChild3 As String = _
    (From el In root...<GrandChild3> _
    Select el).First()
Console.WriteLine(grandChild3)
```

<span data-ttu-id="cdc1f-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cdc1f-108">This example produces the following output:</span></span>

```output
GC3 Value
```

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="cdc1f-109">Örnek: XML 'in bir ad alanında olduğunu bul</span><span class="sxs-lookup"><span data-stu-id="cdc1f-109">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="cdc1f-110">Aşağıdaki örnek, öncekiyle aynı şekilde, ancak bir ad alanında olan XML için de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cdc1f-110">The following example does the same as the previous one, but for XML that's  in a namespace.</span></span> <span data-ttu-id="cdc1f-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cdc1f-111">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
  <aw:Child1>
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
  </aw:Child1>
  <aw:Child2>
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
  </aw:Child2>
  <aw:Child3>
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
  </aw:Child3>
  <aw:Child4>
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
  </aw:Child4>
</aw:Root>");
XNamespace aw = "http://www.adventure-works.com";
string grandChild3 = (string)
    (from el in root.Descendants(aw + "GrandChild3")
     select el).First();
Console.WriteLine(grandChild3);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child1>
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
                </aw:Child1>
                <aw:Child2>
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
                </aw:Child2>
                <aw:Child3>
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
                </aw:Child3>
                <aw:Child4>
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
                </aw:Child4>
            </aw:Root>
        Dim grandChild3 As String = _
            (From el In root...<aw:GrandChild3> _
            Select el).First()
        Console.WriteLine(grandChild3)
    End Sub
End Module
```

<span data-ttu-id="cdc1f-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cdc1f-112">This example produces the following output:</span></span>

```output
GC3 Value
```
