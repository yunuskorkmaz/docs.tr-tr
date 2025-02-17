---
title: Önceki eşdüzey öğeleri bulma-LINQ to XML
description: 'Belirli bir öğeden önce gelen eşdüzey öğeleri bulmayı öğrenin. İki yöntem gösteriliyor: biri önceki eşdüzey eksen üzerinde XPathSelectElements kullanır, diğeri XNode. ElementsBeforeSelf kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 0cfd516f274eaf2940a7b944d34c6ea494e7eaa1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546191"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a>Önceki eşdüzey öğeleri bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> , belirli bir öğeden önce gelen eşdüzey öğeleri bulmak ve <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> aynı öğeleri bulmak için kullanmak üzere önceki eşdüzey eksen üzerinde nasıl kullanılacağı gösterilmektedir.

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a>Örnek: bir öğeden önce gelen eşdüzey öğeleri bulmak için iki yöntem kullanın

Aşağıdaki örnek, `FullAddress` XML belgesi [örnek xml dosyasında öğesini bulur: müşteriler ve siparişler](sample-xml-file-customers-orders.md)ve önceki eşdüzey öğeleri iki farklı şekilde alır. Ardından sonuçları karşılaştırır ve özdeş olarak bulur.

> [!NOTE]
> Her iki yöntem de belge düzeninde olan sonuçlar sağlar.

Kullanılan XPath ifadesi `preceding-sibling::*` .

```csharp
XElement co = XElement.Load("CustomersOrders.xml");

XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");

// LINQ to XML query
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();

// XPath expression
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim add As XElement = co.<Customers>.<Customer>. _
        <FullAddress>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
