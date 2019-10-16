---
title: 'Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: f56ec18933856d862f9ef9630ce3d33805f96894
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321311"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)
Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır. Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.  
  
 @No__t-1 sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi, belirtilen ada sahip <xref:System.Xml.Linq.XAttribute> değerini döndürür.  
  
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
  
 Bu örnek, ağaçtaki `Phone` adlı tüm alt öğeleri bulur ve sonra `type` adlı özniteliği bulur.  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
home  
work  
```  
  
## <a name="example"></a>Örnek  
 Özniteliğin değerini almak istiyorsanız, <xref:System.Xml.Linq.XElement> nesneleriyle yaptığınız gibi, bu özniteliği de çevirebilirsiniz. Aşağıdaki örnek bunu gösterir.  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.Linq.XAttribute> sınıfı için `string` ' ye açık atama işleçleri sağlar `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, 0, 1, 2, 3, 4, 5, 6, 7, @no__t 9, 0, 1, 2, 3 ve 4.  
  
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

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
