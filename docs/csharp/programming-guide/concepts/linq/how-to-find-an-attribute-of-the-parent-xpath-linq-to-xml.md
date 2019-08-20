---
title: 'Nasıl yapılır: Üst öğenin bir özniteliğini bulun (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 2e6c124d2653fb4426b3abb693f0b58daa5413c2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593617"
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

```
Results are identical
id="bk101"
```
