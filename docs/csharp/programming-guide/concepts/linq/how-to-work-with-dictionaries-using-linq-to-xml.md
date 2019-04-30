---
title: 'Nasıl yapılır: LINQ to XML kullanarak sözlükleri çalışın (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: a1104d041c72b48a9aad38a489aefe3ec90a16dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701950"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Nasıl yapılır: LINQ to XML kullanarak sözlükleri çalışın (C#)
Genellikle, diğer veri yapılarını XML ve XML veri yapılarını çeşitleri dönüştürmek uygundur. Bu konuda dönüştürerek genel bu yaklaşım, belirli bir uygulama gösterilmektedir. bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir form içinde bir sorgu projelerde yeni bir işlev oluşturma <xref:System.Xml.Linq.XElement> nesneleri ve sonuçta elde edilen koleksiyon geçirilen bağımsız değişken olarak kök oluşturucuya <xref:System.Xml.Linq.XElement> nesne.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
