---
title: XPath (C#) kullanarak LINQ to XML sorgulama
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344805"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>XPath (C#) kullanarak LINQ to XML sorgulama
Bu konu, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır. Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez. XPath sorguları, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları da gerçekleştirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek küçük bir XML ağacı oluşturur ve bir öğe kümesi seçmek için <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> kullanır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  