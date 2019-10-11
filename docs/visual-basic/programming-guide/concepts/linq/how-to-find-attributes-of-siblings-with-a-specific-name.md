---
title: 'Nasıl yapılır: belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 709c21cee37c42f7633b2b108b8846ddd8e3b4e7
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249895"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (Visual Basic)
Bu konu, bağlam düğümünün eşdüzey öğelerinin tüm özniteliklerinin nasıl bulunacağını gösterir. Koleksiyonda yalnızca belirli bir ada sahip öznitelikler döndürülür.  
  
 XPath ifadesi:  
  
 `../Book/@id`  
  
## <a name="example"></a>Örnek  
 Bu örnek önce bir `Book` öğesi bulur ve sonra `Book` adlı tüm eşdüzey öğeleri bulur ve sonra `id` adlı tüm öznitelikleri bulur. Sonuç, özniteliklerin koleksiyonudur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
