---
title: 'Nasıl yapılır: tek bir öznitelik (LINQ-XML) alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: e9e4dce95e9c3202b1cd2a53c186126deac0913c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: tek bir öznitelik (LINQ-XML) alma (Visual Basic)
Bu konuda, bir öğenin tek bir özniteliği öznitelik adı verilen almak açıklanmaktadır. Belirli bir özniteliği olan bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için kullanışlıdır.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A> Yöntemi <xref:System.Xml.Linq.XElement> sınıf döndürür <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi.  
  
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
  
 Bu örnek adlı ağacında tüm alt öğeleri bulur `Phone`ve ardından adlı özniteliği bulur `type`.  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
home  
work  
```  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak istiyorsanız, sahip olduğu gibi çevirebilirsiniz <xref:System.Xml.Linq.XElement> nesneleri. Aşağıdaki örnekte bu gösterir.  
  
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
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Açık atama işleçleri sağlar <xref:System.Xml.Linq.XAttribute> sınıfının `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`ve `GUID?`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanı içinde bir öznitelik için aynı kodu gösterir. Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
