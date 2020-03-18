---
title: Tek bir öznitelik (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168719"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Tek bir öznitelik (LINQ - XML) (C#) nasıl alınır?
Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliği almak için nasıl açıklar. Bu, belirli bir özniteliği olan bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.  
  
 Sınıfın yöntemi belirtilen adla döndürür. <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekyöntemi <xref:System.Xml.Linq.XElement.Attribute%2A> kullanır.  
  
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
  
 Bu örnek, adlı `Phone`ağaçtaki tüm torunları bulur ve sonra `type`adlı özniteliği bulur.  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak istiyorsanız, <xref:System.Xml.Linq.XElement> nesnelerde olduğu gibi onu atabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml.Linq.XAttribute> sınıf için açık döküm `string`operatörleri `bool` `bool?`sağlar `int` `int?`, `uint` `uint?`, `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `GUID` `GUID?`, , , , , , , , , , , , , , , , , , , , , , , `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında bulunan bir öznitelik için aynı kodu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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
  
```output  
home  
work  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
