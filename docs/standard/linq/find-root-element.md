---
title: Kök öğeyi bulma-LINQ to XML
description: C# ve Visual Basic bir XML belgesinin kök öğesini bulmak için XPath ve LINQ to XML nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 16217960b84276bd3bb4c5cb6b38d7cb56d2b41e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553160"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="5a3d1-103">Kök öğeyi bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5a3d1-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="5a3d1-104">Bu makale, bir XML belgesinin kök öğesini bulmak için XPath ve LINQ to XML, C# ve Visual Basic ' de nasıl kullanılacağını gösteren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a3d1-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="5a3d1-105">Örnek: kök öğeyi bulma</span><span class="sxs-lookup"><span data-stu-id="5a3d1-105">Example: Find the root element</span></span>

<span data-ttu-id="5a3d1-106">Bu örnek, XML belgesi örnek XML dosyasında kök öğeyi bulmak için LINQ to XML Query ve XPath kullanır [: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="5a3d1-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="5a3d1-107">XPath ifadesi `/PurchaseOrders` .</span><span class="sxs-lookup"><span data-stu-id="5a3d1-107">The XPath expression is `/PurchaseOrders`.</span></span>

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

<span data-ttu-id="5a3d1-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5a3d1-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="5a3d1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a3d1-109">See also</span></span>

- [<span data-ttu-id="5a3d1-110">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a3d1-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](/../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
