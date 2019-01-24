---
title: 'Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 562f3a40e1670a76778a64570f980326d946a4c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584681"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (C#)
Bu konuda, eşdüzey bağlam düğümünün tüm öznitelikleri bulmak amacıyla gösterilmiştir. Yalnızca belirli bir ada sahip öznitelik koleksiyonu döndürülür.  
  
 XPath ifadesidir:  
  
 `../Book/@id`  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilk bulur bir `Book` öğesi ve bulduğu tüm Eşdüzey öğeleri adlı `Book`ve ardından tüm öznitelikleri adlı bulur `id`. Bir öznitelik koleksiyonu sonucudur.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
