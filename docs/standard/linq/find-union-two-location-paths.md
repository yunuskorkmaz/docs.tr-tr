---
title: İki konum yolunun birleşimini bulma-LINQ to XML
description: 'İki XPath konum yolunun sonuçlarının birleşimini bulmayı öğrenin. İki yöntem gösteriliyor: biri XPathSelectElements kullanır, diğeri Concat standart sorgu işlecini kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 13d1a22d933d789f28efa2d196fc0106986caa90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555009"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a>İki konum yolunun birleşimini bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> , Iki XPath konum yolunun sonuçlarının birleşimini bulmak ve <xref:System.Linq.Enumerable.Concat%2A> Standart sorgu işlecinin aynı şeyi yapmak için nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a>Örnek: tümünü `Category` ve `Price` öğeleri bul ve bunları Birleştir

Bu örnek, `Category` `Price` XML BELGESI örnek XML dosyasındaki tüm öğeleri ve tüm öğeleri bulur [: sayısal veriler](sample-xml-file-numerical-data.md)ve bunları tek bir koleksiyona ekler. XPath ifadesi `//Category|//Price` .

> [!NOTE]
> LINQ to XML sorgu <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları belge sırasına koymak için çağırır. XPath ifadesi sonuçları da belge sırasına göre yapılır.

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

Bu örnek aşağıdaki çıktıyı üretir:

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

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
