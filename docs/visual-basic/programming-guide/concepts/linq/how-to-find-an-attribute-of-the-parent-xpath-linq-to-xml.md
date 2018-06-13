---
title: 'Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: af2b6fc3aaebe4ba45be405c587c549ea73b3289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639369"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (Visual Basic)
Bu konuda, üst öğesine gidin ve bunu bir öznitelik bulunamadı gösterilmektedir.  
  
 XPath ifadesi şöyledir:  
  
 `../@id`  
  
## <a name="example"></a>Örnek  
 Bu örnek ilk bulur bir `Author` öğesi. Ardından bulduğu `id` üst öğesinin özniteliği.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
