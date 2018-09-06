---
title: 'Nasıl yapılır: XML yükleme bir dosyadan (C#)'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: b8322863ad33f8116e26d98467490b9114339553
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746661"
---
# <a name="how-to-load-xml-from-a-file-c"></a>Nasıl yapılır: XML yükleme bir dosyadan (C#)
Bu konuda, XML, kullanarak bir URI'den yüklemek gösterilmektedir <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML belgesi bir dosyadan yüklemek gösterilmektedir. Aşağıdaki örnek, books.xml yükler ve konsola XML ağacı çıkarır.  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
