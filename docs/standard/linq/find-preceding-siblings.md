---
title: Önceki eşdüzey öğeleri bulma-LINQ to XML
description: 'Belirli bir öğeden önce gelen eşdüzey öğeleri bulmayı öğrenin. İki yöntem gösteriliyor: biri önceki eşdüzey eksen üzerinde XPathSelectElements kullanır, diğeri XNode. ElementsBeforeSelf kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 788101eee6cdbce89626d1b46a5011a897c64704
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553189"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a><span data-ttu-id="28dd8-104">Önceki eşdüzey öğeleri bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="28dd8-104">How to find preceding siblings (LINQ to XML)</span></span>

<span data-ttu-id="28dd8-105">Bu makalede <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> , belirli bir öğeden önce gelen eşdüzey öğeleri bulmak ve <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> aynı öğeleri bulmak için kullanmak üzere önceki eşdüzey eksen üzerinde nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28dd8-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> along the preceding-sibling axis to find sibling elements that precede a given element, and how to use <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> to find the same elements.</span></span>

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a><span data-ttu-id="28dd8-106">Örnek: bir öğeden önce gelen eşdüzey öğeleri bulmak için iki yöntem kullanın</span><span class="sxs-lookup"><span data-stu-id="28dd8-106">Example: Use two methods to find sibling elements that precede an element</span></span>

<span data-ttu-id="28dd8-107">Aşağıdaki örnek, `FullAddress` XML belgesi [örnek xml dosyasında öğesini bulur: müşteriler ve siparişler](sample-xml-file-customers-orders.md)ve önceki eşdüzey öğeleri iki farklı şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="28dd8-107">The following example finds the `FullAddress` element in XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), and retrieves the preceding sibling elements in two different ways.</span></span> <span data-ttu-id="28dd8-108">Ardından sonuçları karşılaştırır ve özdeş olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="28dd8-108">It then compares the results and finds them identical.</span></span>

> [!NOTE]
> <span data-ttu-id="28dd8-109">Her iki yöntem de belge düzeninde olan sonuçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="28dd8-109">Both methods provide results that are in document order.</span></span>

<span data-ttu-id="28dd8-110">Kullanılan XPath ifadesi `preceding-sibling::*` .</span><span class="sxs-lookup"><span data-stu-id="28dd8-110">The XPath expression used is `preceding-sibling::*`.</span></span>

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

<span data-ttu-id="28dd8-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="28dd8-111">This example produces the following output:</span></span>

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a><span data-ttu-id="28dd8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28dd8-112">See also</span></span>

- [<span data-ttu-id="28dd8-113">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28dd8-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
