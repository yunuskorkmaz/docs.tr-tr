---
title: Belirli bir ada sahip kardeşlerin özniteliklerini bulma (XPath-LINQ- XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 331e1a7f432f4d06b697180b1594106ec6842c9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169265"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Belirli bir ada sahip kardeşlerin özniteliklerini bulma (XPath-LINQ- XML) (C#)
Bu konu, bağlam düğümünün kardeşlerinin tüm özniteliklerini nasıl bulabileceğinizi gösterir. Yalnızca belirli bir ada sahip öznitelikler koleksiyonda döndürülür.  
  
 XPath ifadesi:  
  
 `../Book/@id`  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Book` önce bir öğe yi bulur, sonra adlı `Book`tüm `id`kardeş öğeleri bulur ve sonra adlı tüm öznitelikleri bulur. Sonuç özniteliklerin bir koleksiyondur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  