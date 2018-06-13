---
title: 'Nasıl yapılır: LINQ-XML (C#) kullanarak sözlükler ile çalışma'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 3f3b2a19f2527ef5d2fececf916c09256e90af7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319877"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Nasıl yapılır: LINQ-XML (C#) kullanarak sözlükler ile çalışma
Genellikle, diğer veri yapılarını XML ve XML veri yapılarını çeşitleri dönüştürmek uygundur. Bu konu, dönüştürerek genel bu yaklaşım, belirli bir uygulamasına gösterir bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sorgu projeleri yeni işlev yapım biçimi kullanır <xref:System.Xml.Linq.XElement> nesneleri ve sonuçta elde edilen koleksiyonu geçirilen bağımsız değişken olarak kök oluşturucuya <xref:System.Xml.Linq.XElement> nesnesi.  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, XML'den bir sözlük oluşturur.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
