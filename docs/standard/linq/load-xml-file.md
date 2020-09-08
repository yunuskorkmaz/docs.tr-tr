---
title: Dosyadan XML yükleme-LINQ to XML
description: C# ' de XElement. Load yöntemini ve bir dosyadan XML belgesi yüklemek için Visual Basic kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 7ac77205eb1f7637982e8f40d31df0a422ecba22
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553301"
---
# <a name="how-to-load-xml-from-a-file-linq-to-xml"></a><span data-ttu-id="b02fe-103">Dosyadan XML yükleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b02fe-103">How to load XML from a file (LINQ to XML)</span></span>

<span data-ttu-id="b02fe-104">Bu makalede, C# ' deki bir dosyadan XML yükleme ve yöntemi kullanılarak Visual Basic gösterilmektedir <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b02fe-104">This article shows how to load XML from a file in C# and Visual Basic using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-load-xml-document-from-a-file"></a><span data-ttu-id="b02fe-105">Örnek: XML belgesini bir dosyadan yükle</span><span class="sxs-lookup"><span data-stu-id="b02fe-105">Example: Load XML document from a file</span></span>

<span data-ttu-id="b02fe-106">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> dosyaya başvuruda bulunan URI ile birlikte sağlayarak bir dosyanın BIR XML belgesinin nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b02fe-106">The following example shows how to load an XML document from a file by providing <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> with the URI that references the file.</span></span> <span data-ttu-id="b02fe-107">Örnek, books.xml yükler ve konsola XML ağacını verir.</span><span class="sxs-lookup"><span data-stu-id="b02fe-107">The example loads books.xml and outputs the XML tree to the console.</span></span>

<span data-ttu-id="b02fe-108">books.xml içeriği [örnek xml dosyasında gösterilir: kitaplar](sample-xml-file-books.md).</span><span class="sxs-lookup"><span data-stu-id="b02fe-108">The contents of books.xml are shown in [Sample XML file: Books](sample-xml-file-books.md).</span></span>

```csharp
XElement booksFromFile = XElement.Load(@"books.xml");
Console.WriteLine(booksFromFile);
```

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

<span data-ttu-id="b02fe-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b02fe-109">This example produces the following output:</span></span>

```xml
<Catalog>
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
</Catalog>
```
