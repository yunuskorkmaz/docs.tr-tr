---
title: 'Nasıl yapılır: LINQ to XML (Visual Basic) XPath kullanarak sorgula'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244354"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Nasıl yapılır: LINQ to XML (Visual Basic) XPath kullanarak sorgula
Bu konu, bir XML ağacı XPath kullanarak sorgula olanak tanıyan uzantı yöntemleri tanıtır. Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Kullanarak sorgulamak için çok özel bir nedeniniz yoksa, XPath XPath ile LINQ to XML kullanarak eski kod kapsamlı kullanımını gibi önerilmez. XPath sorguları gerçekleştirme yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, küçük bir XML ağacı oluşturur ve kullanır <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> öğe kümesini seçin.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
