---
title: 'Nasıl yapılır: (XPath-LINQ to XML) eşdüzey düğümleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: d225b30b8bfcae09c5824d974e194f8a06ddfc86
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485394"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a>Nasıl yapılır: (XPath-LINQ to XML) eşdüzey düğümleri bulma (C#)
Belirli bir ada sahip tüm bir düğümün eşdüzey bulmak isteyebilirsiniz. Bağlam düğümünün belirli bir ada sahipse, sonuçta elde edilen koleksiyon bağlam düğümünün içerebilir.  
  
 XPath ifadesidir:  
  
 `../Book`  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilk bulur bir `Book` öğesi ve bulduğu tüm Eşdüzey öğeleri adlı `Book`. Sonuçta elde edilen koleksiyon bağlam düğümü içerir.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
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
```  
