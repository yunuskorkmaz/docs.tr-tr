---
title: İsteğe bağlı bir öğeyi filtreleme-LINQ to XML
description: Bir alt öğe için arama, öğe mevcut olmadığında aramanın bir özel durumu tetikleyemeyen bir şekilde yazılabilir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0bf4a2f2c1db420492939351795e3b66b9e0b6b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547310"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a><span data-ttu-id="f6b53-103">İsteğe bağlı bir öğeyi filtreleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f6b53-103">How to filter on an optional element (LINQ to XML)</span></span>

<span data-ttu-id="f6b53-104">Bazen, XML belgenizde bulunduğundan emin olmadığınız halde bir öğe için filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6b53-104">Sometimes you want to filter for an element even though you're not sure it exists in your XML document.</span></span> <span data-ttu-id="f6b53-105">Aramanızı yazarak, belirli bir öğe alt öğeye sahip olmasa bile, filtre uygulayarak null başvuru özel durumu tetiklememeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6b53-105">You can write your search so that, even if the particular element doesn't have the child element, you don't trigger a null reference exception by filtering for it.</span></span>

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a><span data-ttu-id="f6b53-106">Örnek: hedef öğe yoksa bir özel durum tetiklemeyen arama</span><span class="sxs-lookup"><span data-stu-id="f6b53-106">Example: Search that doesn't trigger an exception when the target element doesn't exist</span></span>

<span data-ttu-id="f6b53-107">Aşağıdaki örnekte, `Child5` öğesinin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f6b53-107">In the following example, the `Child5` element doesn't have a `Type` child element, but the query still executes correctly.</span></span> <span data-ttu-id="f6b53-108">Örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6b53-108">The example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

<span data-ttu-id="f6b53-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f6b53-109">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a><span data-ttu-id="f6b53-110">Örnek: bir ad alanında XML için aynı arama ancak</span><span class="sxs-lookup"><span data-stu-id="f6b53-110">Example: Same search but for XML in a namespace</span></span>

<span data-ttu-id="f6b53-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorgu ancak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f6b53-111">The following example is the same query but for XML that's in a namespace.</span></span> <span data-ttu-id="f6b53-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f6b53-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

<span data-ttu-id="f6b53-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f6b53-113">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a><span data-ttu-id="f6b53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b53-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f6b53-115">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f6b53-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f6b53-116">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f6b53-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="f6b53-117">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b53-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
- [<span data-ttu-id="f6b53-118">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b53-118">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="f6b53-119">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b53-119">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="f6b53-120">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="f6b53-120">XML Value Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="f6b53-121">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b53-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f6b53-122">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b53-122">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
