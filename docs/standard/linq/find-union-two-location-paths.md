---
title: İki konum yolunun birleşimini bulma-LINQ to XML
description: 'İki XPath konum yolunun sonuçlarının birleşimini bulmayı öğrenin. İki yöntem gösteriliyor: biri XPathSelectElements kullanır, diğeri Concat standart sorgu işlecini kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ba2a1eef73a586074c75a7fec84c912acb8b25e9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553100"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a><span data-ttu-id="88a86-104">İki konum yolunun birleşimini bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="88a86-104">How to find a union of two location paths (LINQ to XML)</span></span>

<span data-ttu-id="88a86-105">Bu makalede <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> , Iki XPath konum yolunun sonuçlarının birleşimini bulmak ve <xref:System.Linq.Enumerable.Concat%2A> Standart sorgu işlecinin aynı şeyi yapmak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88a86-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find the union of the results of two XPath location paths, and how to use the <xref:System.Linq.Enumerable.Concat%2A> standard query operator to do the same thing.</span></span>

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a><span data-ttu-id="88a86-106">Örnek: tümünü `Category` ve `Price` öğeleri bul ve bunları Birleştir</span><span class="sxs-lookup"><span data-stu-id="88a86-106">Example: Find all `Category` and `Price` elements and concatenate them</span></span>

<span data-ttu-id="88a86-107">Bu örnek, `Category` `Price` XML BELGESI örnek XML dosyasındaki tüm öğeleri ve tüm öğeleri bulur [: sayısal veriler](sample-xml-file-numerical-data.md)ve bunları tek bir koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="88a86-107">This example finds all of the `Category` elements and all of the `Price` elements in XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md), and concatenates them into a single collection.</span></span> <span data-ttu-id="88a86-108">XPath ifadesi `//Category|//Price` .</span><span class="sxs-lookup"><span data-stu-id="88a86-108">The XPath expression is `//Category|//Price`.</span></span>

> [!NOTE]
> <span data-ttu-id="88a86-109">LINQ to XML sorgu <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları belge sırasına koymak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="88a86-109">The LINQ to XML query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to put the results in document order.</span></span> <span data-ttu-id="88a86-110">XPath ifadesi sonuçları da belge sırasına göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="88a86-110">The XPath expression results are also in document order.</span></span>

```csharp
XDocument data = XDocument.Load("Data.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    data
    .Descendants("Category")
    .Concat(
        data
        .Descendants("Price")
    )
    .InDocumentOrder();

// XPath expression
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim data As XDocument = XDocument.Load("Data.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    data...<Category>.Concat(data...<Price>).InDocumentOrder()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    data.XPathSelectElements("//Category|//Price")

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

<span data-ttu-id="88a86-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88a86-111">This example produces the following output:</span></span>

```output
Results are identical
<Category>A</Category>
<Price>24.50</Price>
<Category>B</Category>
<Price>89.99</Price>
<Category>A</Category>
<Price>4.95</Price>
<Category>A</Category>
<Price>66.00</Price>
<Category>B</Category>
<Price>.99</Price>
<Category>A</Category>
<Price>29.00</Price>
<Category>B</Category>
<Price>6.99</Price>
```

## <a name="see-also"></a><span data-ttu-id="88a86-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a86-112">See also</span></span>

- [<span data-ttu-id="88a86-113">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88a86-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
