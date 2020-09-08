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
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a>Hemen önceki eşdüzey öğeyi bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , bir düğümden hemen önce gelen eşdüzey öğeyi bulmak için nasıl kullanılacağı ve aynı şeyi yapmak için LINQ to XML sorgusunun nasıl kullanılacağı gösterilmektedir. LINQ to XML aksine, XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle, bu daha ilginç karşılaştırmalardan biridir.

## <a name="example-find-the-next-to-last-element"></a>Örnek: son öğenin yanına bul

Bu örnekte, LINQ to XML sorgusu, <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen koleksiyondaki son düğümü bulmak için işlecini kullanır <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> . Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
