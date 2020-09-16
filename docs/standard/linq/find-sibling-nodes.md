---
title: Eşdüzey düğümleri bulma-LINQ to XML
description: 'Belirli bir ada sahip bir düğümün tüm eşdüzey öğelerinin nasıl bulunacağını öğrenin. İki yöntem gösteriliyor: biri XPathSelectElements kullanır, diğeri LINQ to XML sorgu kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 56833ef3758a6d8af1eb6f0a103b85ad967c9aad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555913"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a>Eşdüzey düğümleri bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> , belirli bir ada sahip bir düğümün tüm eşdüzey öğelerinin bulunması ve LINQ to XML sorgusunun aynı şeyi yapmak için nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> Elde edilen koleksiyon, aynı zamanda belirli bir ada sahipse, bağlam düğümünü içerir.

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a>Örnek: adlı bir öğesi `Book` ve adlı tüm eşdüzey öğeleri bulun `Book`

Bu örnek ilk `Book` olarak XML belgesi [örnek xml dosyasında](sample-xml-file-books.md)bir öğe bulur: kitaplar ve sonra adlı tüm eşdüzey öğeleri bulur `Book` . Elde edilen koleksiyon, bağlam düğümünü içerir.

XPath ifadesi `../Book`

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Elements("Book")
    .Skip(1)
    .First();

// LINQ to XML query
IEnumerable<XElement> list1 =
    book
    .Parent
    .Elements("Book");

// XPath expression
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

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
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
