---
title: 'Nasıl yapılır: Tek Bir Öznitelik Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397862"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)
Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır. Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> Sınıfının yöntemi, <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip öğesini döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemini kullanır.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 Bu örnek adlı ağaçtaki tüm alt öğeleri bulur `Phone` ve sonra adlı özniteliği bulur `type` .  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
home  
work  
```  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak istiyorsanız, nesneleri ile yaptığınız gibi, bu özniteliği de çevirebilirsiniz <xref:System.Xml.Linq.XElement> . Aşağıdaki örnek bunu gösterir.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)],,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` ,, `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,,,,,,,, ve için  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
