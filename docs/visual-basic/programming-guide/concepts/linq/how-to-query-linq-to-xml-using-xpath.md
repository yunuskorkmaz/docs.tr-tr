---
title: 'Nasıl yapılır: XPath Kullanarak LINQ to XML Sorgulama'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d95e5a82d146c357f52d03375119474b042d49f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397927"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Nasıl yapılır: XPath kullanarak LINQ to XML sorgulama (Visual Basic)
Bu konu, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır. Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> ..  
  
 Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez. XPath sorguları, sorgu ve sorgular gerçekleştirmeyecektir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek küçük bir XML ağacı oluşturur ve <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir öğe kümesi seçmek için kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)](advanced-query-techniques-linq-to-xml.md)
