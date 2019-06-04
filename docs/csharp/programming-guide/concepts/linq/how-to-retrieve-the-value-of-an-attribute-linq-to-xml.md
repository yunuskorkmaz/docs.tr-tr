---
title: 'Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 94cab43571f7ade55155e7925975f253e452ceb7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484999"
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
 Aşağıdaki örnekte, öznitelik bir ad alanında olduğu bir özniteliğin değerini almak nasıl gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
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

- [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
