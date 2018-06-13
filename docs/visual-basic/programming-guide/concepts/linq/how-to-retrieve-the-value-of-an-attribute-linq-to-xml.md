---
title: 'Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 96d5e5a0c7ee294b140385c93b13ee56f3f92491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642960"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (Visual Basic)
Bu konu özniteliklerin değeri elde etme gösterir. Başlıca iki yolu vardır: dönüştürmek bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüşüm işleci sonra içeriği öğesi veya özniteliği belirtilen türe dönüştürür. Alternatif olarak, kullanabileceğiniz <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği. Ancak, atama genellikle daha iyi yaklaşımdır. Boş değer atanabilir bir tür için öznitelik atama, kodu olabilir ya da var olmayabilir bir özniteliğin değeri alınırken yazma daha basittir. Bu teknik örnekleri için bkz: [nasıl yapılır: bir öğenin (LINQ-XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Visual Basic'te bir öznitelik değerini almak için tümleşik özniteliği özelliğini kullanabilirsiniz.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliği'ni kullanabilirsiniz. Ayrıca, var olmayan bir öznitelik değerini ayarlamak için tümleşik özniteliği özelliğini kullanırsanız, öznitelik oluşturulur.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir öznitelik değerini almak öznitelik bir ad alanındaki olduğu gösterilmektedir. Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
