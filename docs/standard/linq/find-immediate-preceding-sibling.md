---
title: Hemen önceki eşdüzey öğeyi bulma-LINQ to XML
description: 'Bir düğümden hemen önce gelen eşdüzey öğeyi bulmayı bulma hakkında bilgi edinin. İki yöntem gösteriliyor: biri XPathEvaluate kullanır, diğeri LINQ to XML sorgu kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: ca3f7bea150ebcfab100475ceb13b1624c91094f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553197"
---
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a><span data-ttu-id="0261e-104">Hemen önceki eşdüzey öğeyi bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0261e-104">How to find the immediate preceding sibling (LINQ to XML)</span></span>

<span data-ttu-id="0261e-105">Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , bir düğümden hemen önce gelen eşdüzey öğeyi bulmak için nasıl kullanılacağı ve aynı şeyi yapmak için LINQ to XML sorgusunun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0261e-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the sibling that immediately precedes a node, and how to use LINQ to XML query to do the same thing.</span></span> <span data-ttu-id="0261e-106">LINQ to XML aksine, XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle, bu daha ilginç karşılaştırmalardan biridir.</span><span class="sxs-lookup"><span data-stu-id="0261e-106">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to LINQ to XML, this is one of the more interesting comparisons.</span></span>

## <a name="example-find-the-next-to-last-element"></a><span data-ttu-id="0261e-107">Örnek: son öğenin yanına bul</span><span class="sxs-lookup"><span data-stu-id="0261e-107">Example: Find the next to last element</span></span>

<span data-ttu-id="0261e-108">Bu örnekte, LINQ to XML sorgusu, <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen koleksiyondaki son düğümü bulmak için işlecini kullanır <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="0261e-108">In this example, the LINQ to XML query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="0261e-109">Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="0261e-109">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

```csharp
XElement root = XElement.Parse(
    @"<Root>
    <Child1/>
    <Child2/>
    <Child3/>
    <Child4/>
</Root>");
XElement child4 = root.Element("Child4");

// LINQ to XML query
XElement el1 =
    child4
    .ElementsBeforeSelf()
    .Last();

// XPath expression
XElement el2 =
    ((IEnumerable)child4
                 .XPathEvaluate("preceding-sibling::*[1]"))
                 .Cast<XElement>()
                 .First();

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="0261e-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0261e-110">This example produces the following output:</span></span>

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="0261e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0261e-111">See also</span></span>

- [<span data-ttu-id="0261e-112">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0261e-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
