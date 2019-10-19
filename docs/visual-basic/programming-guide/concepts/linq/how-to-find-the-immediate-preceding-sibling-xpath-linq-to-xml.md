---
title: 'Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 46f5b0d2d32e8dcba5f8c9e164a027a8e8118f4d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582699"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b0ead-102">Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0ead-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="b0ead-103">Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ead-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="b0ead-104">@No__t_0 aksine, XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle, bu daha ilginç karşılaştırmalardan biridir.</span><span class="sxs-lookup"><span data-stu-id="b0ead-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>

## <a name="example"></a><span data-ttu-id="b0ead-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0ead-105">Example</span></span>

<span data-ttu-id="b0ead-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusu <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> tarafından döndürülen koleksiyondaki son düğümü bulmak için <xref:System.Linq.Enumerable.Last%2A> işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0ead-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="b0ead-107">Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0ead-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

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

<span data-ttu-id="b0ead-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b0ead-108">This example produces the following output:</span></span>

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="b0ead-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0ead-109">See also</span></span>

- [<span data-ttu-id="b0ead-110">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0ead-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
