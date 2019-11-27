---
title: 'Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: b2cb9efba0ef65a1b1ab1d7dadd54759f7d2a26b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344618"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (Visual Basic)

Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aksine, XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle, bu daha ilginç karşılaştırmalardan biridir.

## <a name="example"></a>Örnek

Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusu <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>tarafından döndürülen koleksiyondaki son düğümü bulmak için <xref:System.Linq.Enumerable.Last%2A> işlecini kullanır. Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.

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

Bu örnek aşağıdaki çıktıyı üretir:

```console
Results are identical
<Child3 />
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
