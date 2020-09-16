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
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="9ebd9-103">Kök öğeyi bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9ebd9-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="9ebd9-104">Bu makale, bir XML belgesinin kök öğesini bulmak için XPath ve LINQ to XML, C# ve Visual Basic ' de nasıl kullanılacağını gösteren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ebd9-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="9ebd9-105">Örnek: kök öğeyi bulma</span><span class="sxs-lookup"><span data-stu-id="9ebd9-105">Example: Find the root element</span></span>

<span data-ttu-id="9ebd9-106">Bu örnek, XML belgesi örnek XML dosyasında kök öğeyi bulmak için LINQ to XML Query ve XPath kullanır [: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="9ebd9-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="9ebd9-107">XPath ifadesi `/PurchaseOrders` .</span><span class="sxs-lookup"><span data-stu-id="9ebd9-107">The XPath expression is `/PurchaseOrders`.</span></span>

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

<span data-ttu-id="9ebd9-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9ebd9-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="9ebd9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ebd9-109">See also</span></span>

- [<span data-ttu-id="9ebd9-110">XPath ile LINQ to XML Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="9ebd9-110">Comparison of XPath and LINQ to XML</span></span>](comparison-xpath-linq-xml.md)
