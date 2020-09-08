---
title: Belirli bir özniteliğe sahip öğeleri bulma-LINQ to XML
description: 'Belirli bir özniteliğe (değerden bağımsız olarak) sahip olan tüm öğeleri bulmayı öğrenin. İki yöntem gösteriliyor: biri XPathEvaluate kullanır, diğeri LINQ to XML sorgu kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: fc9f5acdda457eea1790f76695a71afe5fefa070
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552859"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a>Belirli bir özniteliğe sahip öğeleri bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , belirli bir özniteliğe (değerden bağımsız olarak) sahip tüm öğeleri bulmak için nasıl kullanılacağı ve LINQ to XML sorgusunun aynı şeyi yapmak için nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-all-elements-that-have-the-select-attribute"></a>Örnek: özniteliği olan tüm öğeleri bul `Select`

Aşağıdaki örnek bir XML ağacı oluşturur ve özniteliği olan öğeleri bulur `Select` .

XPath ifadesi `./*[@Select]` .

```csharp
XElement doc = XElement.Parse(
@"<Root>
    <Child1>1</Child1>
    <Child2 Select='true'>2</Child2>
    <Child3>3</Child3>
    <Child4 Select='true'>4</Child4>
    <Child5>5</Child5>
</Root>");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in doc.Elements()
    where el.Attribute("Select") != null
    select el;

// XPath expression
IEnumerable<XElement> list2 =
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim doc As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2 Select='true'>2</Child2>
        <Child3>3</Child3>
        <Child4 Select='true'>4</Child4>
        <Child5>5</Child5>
    </Root>

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In doc.Elements() _
    Where el.@Select <> Nothing _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()

If list1.Count() = list2.Count() And _
    list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
