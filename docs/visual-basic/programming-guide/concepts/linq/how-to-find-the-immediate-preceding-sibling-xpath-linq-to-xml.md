---
title: 'Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 47ba557343d0f691c2ee0f2c56102df313ecfb30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641121"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) bulunamadı (Visual Basic)
Bazen bir düğüme hemen önceki eşdüzey bulmak istediğiniz. XPath tersine önceki eşdüzey eksenlerin konumsal koşulları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilginç karşılaştırmaları biridir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullanır <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen bir koleksiyondaki son düğümünü bulmayı işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Bunun aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerine sahip bir koşul kullanır.  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
