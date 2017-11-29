---
title: "Nasıl yapılır: LINQ-XML XPath (C#) kullanarak sorgulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cb47b5b4b85536feeb5006fe6dd31580ca651b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Nasıl yapılır: LINQ-XML XPath (C#) kullanarak sorgulama
Bu konu, bir XML ağacı XPath kullanarak sorgula sağlayan genişletme yöntemleri tanıtır. Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz: <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Kullanarak sorgulamak için çok özel bir nedeniniz yoksa XPath, LINQ-XML XPath kullanarak eski kod kapsamlı kullanımını gibi önerilmez. XPath sorguları değil gerçekleştirecek yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte küçük bir XML ağacı oluşturduğu ve kullandığı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir grup öğeyi seçin.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş sorgu teknikler (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
