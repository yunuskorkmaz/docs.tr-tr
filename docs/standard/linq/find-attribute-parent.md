---
title: Üst LINQ to XML bir özniteliği bulma
description: 'Bir öğeye gitmeyi ve üst öğesinin bir özniteliğini bulmayı öğrenin. İki yöntem gösteriliyor: biri XPathEvaluate kullanır, diğeri LINQ to XML sorgu kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 811766ecfdf2f080f29f21ae08981483f75a7e44
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553945"
---
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a>Üst öğenin bir özniteliğini bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , bir üst öğenin özniteliğini bulmak için nasıl kullanılacağı ve aynı şeyi yapmak için LINQ to XML sorgusunun nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a>Örnek: öğesini bulun `Author` ve sonra `id` üst öğesinin özniteliğini bulun

Bu örnek ilk olarak `Author` XML belgesi [örnek xml dosyasında](sample-xml-file-books.md)bir öğe bulur: kitaplar ve sonra `id` üst öğesinin özniteliğini bulur.

XPath ifadesi `../@id` .

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()

' LINQ to XML query
Dim att1 As XAttribute = author.Parent.Attribute("id")

' XPath expression
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _
    IEnumerable).Cast(Of XAttribute)().First()

If att1 Is att2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(att1)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
