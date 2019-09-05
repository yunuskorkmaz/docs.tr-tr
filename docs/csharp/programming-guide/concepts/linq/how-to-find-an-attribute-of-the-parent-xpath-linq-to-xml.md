---
title: 'Nasıl yapılır: Üst öğenin bir özniteliğini bulun (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: aa602f6876b014c48a73dea9b2ff42eb953e5c4c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253768"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Nasıl yapılır: Üst öğenin bir özniteliğini bulun (XPath-LINQ to XML) (C#)

Bu konu başlığı altında, üst öğeye gitme ve bir özniteliği bulma gösterilmektedir.

XPath ifadesi:

`../@id`

## <a name="example"></a>Örnek

Bu örnek önce bir `Author` öğesi bulur. Daha sonra üst öğenin `id` özniteliğini bulur.

Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
id="bk101"
```
