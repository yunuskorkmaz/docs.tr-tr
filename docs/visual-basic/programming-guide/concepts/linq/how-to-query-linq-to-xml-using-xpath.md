---
title: 'Nasıl yapılır: XPath kullanarak LINQ to XML sorgulama'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 563756c019ddd458d46f47c843e32ddc7bbaacd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347652"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Nasıl yapılır: XPath kullanarak LINQ to XML sorgulama (Visual Basic)
Bu konu, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır. Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez. XPath sorguları, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları da gerçekleştirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek küçük bir XML ağacı oluşturur ve bir öğe kümesi seçmek için <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> kullanır.  
  
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

- [Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
