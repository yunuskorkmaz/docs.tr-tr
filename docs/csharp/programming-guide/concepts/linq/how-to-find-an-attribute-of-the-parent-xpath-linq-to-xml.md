---
title: Üst öğenin bir özniteliğini bulma (XPath-LINQ to XML) (C#)
description: Üst öğenin bir özniteliğini bulmayı öğrenin. Örnek bir XML belgesi kullanan bir kod örneğine bakın.
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303302"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Üst öğenin bir özniteliğini bulma (XPath-LINQ to XML) (C#)

Bu konu başlığı altında, üst öğeye gitme ve bir özniteliği bulma gösterilmektedir.

XPath ifadesi:

`../@id`

## <a name="example"></a>Örnek

Bu örnek önce bir `Author` öğesi bulur. Daha sonra `id` üst öğenin özniteliğini bulur.

Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).

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
