---
title: Kök öğeyi bulma-LINQ to XML
description: C# ve Visual Basic bir XML belgesinin kök öğesini bulmak için XPath ve LINQ to XML nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 89247c19fc31add4e95f11742772cef1bdd2ce63
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679468"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a>Kök öğeyi bulma (LINQ to XML)

Bu makale, bir XML belgesinin kök öğesini bulmak için XPath ve LINQ to XML, C# ve Visual Basic ' de nasıl kullanılacağını gösteren bir örnek sağlar.

## <a name="example-find-the-root-element"></a>Örnek: kök öğeyi bulma

Bu örnek, XML belgesi örnek XML dosyasında kök öğeyi bulmak için LINQ to XML Query ve XPath kullanır [: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md). XPath ifadesi `/PurchaseOrders` .

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath ile LINQ to XML Karşılaştırması](comparison-xpath-linq-xml.md)
