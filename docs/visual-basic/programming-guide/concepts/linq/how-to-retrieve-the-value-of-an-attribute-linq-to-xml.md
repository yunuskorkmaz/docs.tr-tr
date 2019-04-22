---
title: 'Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 7cdd3e1f3e4c15d99511e944fd9bc2faac17dc5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824375"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (Visual Basic)
Bu konuda, öznitelik değerini elde etme gösterilmektedir. Başlıca iki yolu vardır: Edebilirsiniz bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüştürme operatörü sonra içeriği öğe veya öznitelik belirtilen türe dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği. Ancak, atama, genellikle daha iyi bir yaklaşım değildir. Öznitelik boş değer atanabilir bir tür için tür dönüştürme, kod var olmayabilir veya bir özniteliğin değeri alınırken yazmak kolaydır. Bu tekniğe ilişkin örnekler için bkz [nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, tümleşik öznitelik özelliği bir özniteliğin değerini almak için kullanabilirsiniz.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, tümleşik öznitelik özelliği bir özniteliğin değerini ayarlamak için kullanabilirsiniz. Ayrıca, mevcut olmayan bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliği kullanırsanız, öznitelik oluşturulur.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, öznitelik bir ad alanında olduğu bir özniteliğin değerini almak nasıl gösterir. Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
