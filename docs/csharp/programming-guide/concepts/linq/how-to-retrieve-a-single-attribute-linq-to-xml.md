---
title: 'Nasıl yapılır: Tek bir öznitelik al (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4a1be51c7f0e89a8f211ae523eb102282bd9747b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592653"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Nasıl yapılır: Tek bir öznitelik al (LINQ to XML) (C#)
Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır. Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.  
  
 Sınıfının yöntemi ,<xref:System.Xml.Linq.XAttribute>belirtilen ada <xref:System.Xml.Linq.XElement.Attribute%2A>sahipöğesinidöndürür. <xref:System.Xml.Linq.XElement>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemini kullanır.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Bu örnek adlı `Phone`ağaçtaki tüm alt öğeleri bulur ve sonra adlı `type`özniteliği bulur.  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
home  
work  
```  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak istiyorsanız, nesneleri ile <xref:System.Xml.Linq.XElement> yaptığınız gibi, bu özniteliği de çevirebilirsiniz. Aşağıdaki örnek bunu gösterir.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml.Linq.XAttribute> sınıfına`bool?`, ,,`uint?`,,,,, ,,,,,,,,,,,,`long?` `bool` `string` `int` `int?` `uint` `long` `ulong` ,,,`double?` ,`TimeSpan`,, ,`decimal` ,`GUID`,,, ,`TimeSpan?`, ve `DateTime` `decimal?` `float?` `double` `ulong?` `float` `DateTime?`  `GUID?`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
