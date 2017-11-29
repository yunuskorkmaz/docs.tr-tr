---
title: "Nasıl yapılır: LINQ-XML (Visual Basic) XPath kullanarak sorgula"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f885a76a79832b06f2f5d4a270d418bf244cb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Nasıl yapılır: LINQ-XML (Visual Basic) XPath kullanarak sorgula
Bu konu, bir XML ağacı XPath kullanarak sorgula sağlayan genişletme yöntemleri tanıtır. Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz: <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Kullanarak sorgulamak için çok özel bir nedeniniz yoksa XPath, LINQ-XML XPath kullanarak eski kod kapsamlı kullanımını gibi önerilmez. XPath sorguları değil gerçekleştirecek yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte küçük bir XML ağacı oluşturduğu ve kullandığı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir grup öğeyi seçin.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
