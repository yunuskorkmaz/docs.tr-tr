---
title: 'Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: f30c810483d8253132b9fe3e0959d04a8b4d26a0
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690067"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="e65f3-102">Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)</span><span class="sxs-lookup"><span data-stu-id="e65f3-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="e65f3-103">Bu konuda, üst öğeye gidin ve bir özniteliğin bulmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e65f3-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="e65f3-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="e65f3-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="e65f3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e65f3-105">Example</span></span>

<span data-ttu-id="e65f3-106">Bu örnekte ilk bulur bir `Author` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e65f3-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="e65f3-107">Ardından bulduğu `id` üst öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e65f3-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="e65f3-108">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e65f3-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="e65f3-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e65f3-109">This example produces the following output:</span></span>

```
Results are identical
id="bk101"
```
