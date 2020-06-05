---
title: 'Nasıl yapılır: Bir Önceki Eşdüzeyi Bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 8b0071b2f39b8debdd52083718fe928c1f9fb6f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364532"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="49a70-102">Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49a70-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="49a70-103">Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49a70-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="49a70-104">XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bu, daha ilginç karşılaştırmalardan biridir.</span><span class="sxs-lookup"><span data-stu-id="49a70-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>

## <a name="example"></a><span data-ttu-id="49a70-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="49a70-105">Example</span></span>

<span data-ttu-id="49a70-106">Bu örnekte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu, <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen koleksiyondaki son düğümü bulmak için işlecini kullanır <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> .</span><span class="sxs-lookup"><span data-stu-id="49a70-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="49a70-107">Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="49a70-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

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

<span data-ttu-id="49a70-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="49a70-108">This example produces the following output:</span></span>

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="49a70-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49a70-109">See also</span></span>

- [<span data-ttu-id="49a70-110">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49a70-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
