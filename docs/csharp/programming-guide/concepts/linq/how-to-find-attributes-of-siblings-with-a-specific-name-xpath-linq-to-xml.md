---
title: 'Nasıl yapılır: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 78795f164490dddd6bdc8dae04961c028228ab0c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593521"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Nasıl yapılır: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bul (XPath-LINQ to XML) (C#)
Bu konu, bağlam düğümünün eşdüzey öğelerinin tüm özniteliklerinin nasıl bulunacağını gösterir. Koleksiyonda yalnızca belirli bir ada sahip öznitelikler döndürülür.  
  
 XPath ifadesi:  
  
 `../Book/@id`  
  
## <a name="example"></a>Örnek  
 Bu örnek önce bir `Book` öğesi bulur, sonra adlı `Book`tüm eşdüzey öğeleri bulur ve sonra adlı `id`tüm öznitelikleri bulur. Sonuç, özniteliklerin koleksiyonudur.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  