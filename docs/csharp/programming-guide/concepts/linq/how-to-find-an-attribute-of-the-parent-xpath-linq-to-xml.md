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
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="75c76-102">Nasıl yapılır: Üst öğenin bir özniteliğini bulun (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="75c76-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="75c76-103">Bu konu başlığı altında, üst öğeye gitme ve bir özniteliği bulma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75c76-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="75c76-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="75c76-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="75c76-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="75c76-105">Example</span></span>

<span data-ttu-id="75c76-106">Bu örnek önce bir `Author` öğesi bulur.</span><span class="sxs-lookup"><span data-stu-id="75c76-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="75c76-107">Daha sonra üst öğenin `id` özniteliğini bulur.</span><span class="sxs-lookup"><span data-stu-id="75c76-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="75c76-108">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="75c76-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="75c76-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="75c76-109">This example produces the following output:</span></span>

```
Results are identical
id="bk101"
```
