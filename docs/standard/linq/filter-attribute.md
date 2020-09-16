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
# <a name="how-to-filter-on-an-attribute-linq-to-xml"></a><span data-ttu-id="ad4d4-103">Bir özniteliğe filtre uygulama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ad4d4-103">How to filter on an attribute (LINQ to XML)</span></span>

<span data-ttu-id="ad4d4-104">Bu makalede, belirtilen bir ad ve öznitelik değerine sahip olan alt öğeleri bulmak için C# ve Visual Basic ' de LINQ to XML sorgusunun ve XPath 'in nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-104">This article shows how to use LINQ to XML query and XPath, in C# and Visual Basic, to find descendant elements that have a specified name and attribute value.</span></span>

## <a name="example-find-all-descendant-elements-that-have-a-specified-name-and-attribute-value"></a><span data-ttu-id="ad4d4-105">Örnek: belirtilen bir ad ve öznitelik değerine sahip tüm alt öğeleri bul</span><span class="sxs-lookup"><span data-stu-id="ad4d4-105">Example: Find all descendant elements that have a specified name and attribute value</span></span>

<span data-ttu-id="ad4d4-106">Bu örnek, XML belgesi örnek XML dosyasında bulunacak LINQ to XML sorgu ve XPath kullanır [: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md), adı olan tüm alt öğeler `Address` ve `Type` değeri "Shipping" olan bir özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-106">This example uses LINQ to XML query and XPath to find, in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md), all descendant elements that have the name `Address`, and a `Type` attribute whose value is "Shipping".</span></span> <span data-ttu-id="ad4d4-107">XPath ifadesi `.//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="ad4d4-107">The XPath expression is `.//Address[@Type='Shipping']`</span></span>

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

<span data-ttu-id="ad4d4-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ad4d4-108">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad4d4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad4d4-109">See also</span></span>

- [<span data-ttu-id="ad4d4-110">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="ad4d4-110">Comparison of XPath and LINQ to XML</span></span>](comparison-xpath-linq-xml.md)
