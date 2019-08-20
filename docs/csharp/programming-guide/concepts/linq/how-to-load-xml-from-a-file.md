---
title: 'Nasıl yapılır: Dosyadan XML yükle (C#)'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: d3e7cdbb0691fafcfcfc684f4495f4785b4ea3e7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593168"
---
# <a name="how-to-load-xml-from-a-file-c"></a>Nasıl yapılır: Dosyadan XML yükle (C#)
Bu konuda, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> yöntemi kullanılarak bir URI 'den XML yükleme gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dosyadan bir XML belgesinin nasıl yükleneceğini gösterir. Aşağıdaki örnek, Books. xml ' i yükler ve XML ağacını konsola çıkarır.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
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
  