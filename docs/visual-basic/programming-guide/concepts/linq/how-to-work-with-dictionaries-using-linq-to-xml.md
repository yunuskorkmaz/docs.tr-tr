---
title: 'Nasıl yapılır: LINQ to XML Kullanarak Sözlüklerle Çalışma'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 14c9c35693f323292849f01af79ae81f92921611
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397680"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>Nasıl yapılır: LINQ to XML kullanarak sözlüklerle çalışma (Visual Basic)
Çok sayıda veri yapısını XML 'e ve XML 'e diğer veri yapılarına dönüştürmek genellikle yararlıdır. Bu konu, bir XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulamasını gösterir <xref:System.Collections.Generic.Dictionary%602> .  
  
## <a name="example"></a>Örnek  
 Bu örnekte, katıştırılmış ifadede XML değişmez değerleri ve bir sorgu kullanılmaktadır. Sorgu yeni <xref:System.Xml.Linq.XElement> nesneler, daha sonra nesne için yeni içerik haline gelir `Root` <xref:System.Xml.Linq.XElement> .  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
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
 Aşağıdaki kod XML 'den bir sözlük oluşturur.  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
