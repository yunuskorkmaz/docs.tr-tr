---
title: Üst öğenin özniteliği (XPath-LINQ'dan XML'e) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141170"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Üst öğenin özniteliği (XPath-LINQ'dan XML'e) (C#) nasıl bulabilirim?

Bu konu, üst öğeye nasıl gidilir ve bir özniteliğini nasıl bulacağını gösterir.

XPath ifadesi:

`../@id`

## <a name="example"></a>Örnek

Bu örnekte `Author` ilk önce bir öğe bulur. Daha sonra `id` üst öğenin özniteliğini bulur.

Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).

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

Bu örnek, aşağıdaki çıktıyı üretir:

```output
Results are identical
id="bk101"
```
