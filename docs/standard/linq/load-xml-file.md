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
# <a name="how-to-load-xml-from-a-file-linq-to-xml"></a>Dosyadan XML yükleme (LINQ to XML)

Bu makalede, C# ' deki bir dosyadan XML yükleme ve yöntemi kullanılarak Visual Basic gösterilmektedir <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .

## <a name="example-load-xml-document-from-a-file"></a>Örnek: XML belgesini bir dosyadan yükle

Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> dosyaya başvuruda bulunan URI ile birlikte sağlayarak bir dosyanın BIR XML belgesinin nasıl yükleneceğini gösterir. Örnek, books.xml yükler ve konsola XML ağacını verir.

books.xml içeriği [örnek xml dosyasında gösterilir: kitaplar](sample-xml-file-books.md).

```csharp
XElement booksFromFile = XElement.Load(@"books.xml");
Console.WriteLine(booksFromFile);
```

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

Bu örnek aşağıdaki çıktıyı üretir:

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
