---
title: 'Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d0babc51dc4992741991be876d0a5ecae8302bd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667723"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (C#)
Bu konuda, öznitelik değerini elde etme gösterilmektedir. Başlıca iki yolu vardır: Edebilirsiniz bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüştürme operatörü sonra içeriği öğe veya öznitelik belirtilen türe dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği. Ancak, atama, genellikle daha iyi bir yaklaşım değildir. Öznitelik boş değer atanabilir bir tür için tür dönüştürme, kod var olmayabilir veya bir özniteliğin değeri alınırken yazmak kolaydır. Bu tekniğe ilişkin örnekler için bkz [nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bir özniteliğin değerini almak için yalnızca cast <xref:System.Xml.Linq.XAttribute> istenen türünüz için nesne.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, öznitelik bir ad alanında olduğu bir özniteliğin değerini almak nasıl gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
