---
title: XPath (C#) kullanarak LINQ'yi XML'e sorgulama
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344805"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>XPath (C#) kullanarak LINQ'yi XML'e sorgulama
Bu konu, XPath kullanarak bir XML ağacısorgulamasağlayan uzantı yöntemlerini tanır. Bu uzantı yöntemlerini kullanma <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>hakkında ayrıntılı bilgi için bkz.  
  
 XPath'i kullanmak için çok özel bir nedeniniz yoksa, örneğin eski kodun yaygın kullanımı gibi, XPath'i LINQ ile XML'e kullanmak önerilmez. XPath sorguları sorguları kadar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] iyi performans göstermez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek küçük bir XML ağacı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> oluşturur ve bir öğe kümesi seçmek için kullanır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  