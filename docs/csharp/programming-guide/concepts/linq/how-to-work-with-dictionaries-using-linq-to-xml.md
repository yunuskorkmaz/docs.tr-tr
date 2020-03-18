---
title: LINQ to XML (C#) kullanarak sözlüklerle nasıl çalışIlir?
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347219"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>LINQ to XML (C#) kullanarak sözlüklerle nasıl çalışIlir?
Veri yapılarının çeşitlerini XML'e, XML'i ise diğer veri yapılarına dönüştürmek genellikle uygundur. Bu konu, bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulama gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, sorgunun yeni <xref:System.Xml.Linq.XElement> nesneleri oluşturduğu ve ortaya çıkan koleksiyonun Kök <xref:System.Xml.Linq.XElement> nesnenin oluşturucusu için bağımsız değişken olarak geçtiği işlevsel bir yapı biçimi kullanır.  
  
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
 Aşağıdaki kod XML bir sözlük oluşturur.  
  
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
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
