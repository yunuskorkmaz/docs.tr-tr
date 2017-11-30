---
title: "Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 12720ca8bd1937d37f8d30400e0b25afa22a40cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (C#)
Bu konu özniteliklerin değeri elde etme gösterir. Başlıca iki yolu vardır: dönüştürmek bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüşüm işleci sonra içeriği öğesi veya özniteliği belirtilen türe dönüştürür. Alternatif olarak, kullanabileceğiniz <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği. Ancak, atama genellikle daha iyi yaklaşımdır. Boş değer atanabilir bir tür için öznitelik atama, kodu olabilir ya da var olmayabilir bir özniteliğin değeri alınırken yazma daha basittir. Bu teknik örnekleri için bkz: [nasıl yapılır: bir öğenin (LINQ-XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak için yalnızca cast <xref:System.Xml.Linq.XAttribute> nesne, istenen türü.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir öznitelik değerini almak öznitelik bir ad alanındaki olduğu gösterilmektedir. Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
