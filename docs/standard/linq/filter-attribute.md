---
title: Bir özniteliğe filtre uygulama-LINQ to XML
description: Bu makalede, belirtilen bir ad ve öznitelik değerine sahip olan alt öğeleri bulmak için C# ve Visual Basic ' de LINQ to XML sorgusunun ve XPath 'in nasıl kullanılacağı gösterilmektedir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: 7d90e047983db1f024884168490e202ed42a85c8
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679475"
---
# <a name="how-to-filter-on-an-attribute-linq-to-xml"></a>Bir özniteliğe filtre uygulama (LINQ to XML)

Bu makalede, belirtilen bir ad ve öznitelik değerine sahip olan alt öğeleri bulmak için C# ve Visual Basic ' de LINQ to XML sorgusunun ve XPath 'in nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-all-descendant-elements-that-have-a-specified-name-and-attribute-value"></a>Örnek: belirtilen bir ad ve öznitelik değerine sahip tüm alt öğeleri bul

Bu örnek, XML belgesi örnek XML dosyasında bulunacak LINQ to XML sorgu ve XPath kullanır [: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md), adı olan tüm alt öğeler `Address` ve `Type` değeri "Shipping" olan bir özniteliği. XPath ifadesi `.//Address[@Type='Shipping']`

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In po...<Address> _
    Where el.@Type = "Shipping" _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    po.XPathSelectElements(".//Address[@Type='Shipping']")

If (list1.Count = list2.Count And _
        list1.Intersect(list2).Count() = list1.Count()) Then
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
<Address Type="Shipping">
  <Name>Ellen Adams</Name>
  <Street>123 Maple Street</Street>
  <City>Mill Valley</City>
  <State>CA</State>
  <Zip>10999</Zip>
  <Country>USA</Country>
</Address>
<Address Type="Shipping">
  <Name>Cristian Osorio</Name>
  <Street>456 Main Street</Street>
  <City>Buffalo</City>
  <State>NY</State>
  <Zip>98112</Zip>
  <Country>USA</Country>
</Address>
<Address Type="Shipping">
  <Name>Jessica Arnold</Name>
  <Street>4055 Madison Ave</Street>
  <City>Seattle</City>
  <State>WA</State>
  <Zip>98112</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath ile LINQ to XML Karşılaştırması](comparison-xpath-linq-xml.md)
