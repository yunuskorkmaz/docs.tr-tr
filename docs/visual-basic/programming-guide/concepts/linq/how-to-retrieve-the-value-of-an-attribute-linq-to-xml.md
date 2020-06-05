---
title: 'Nasıl yapılır: Öznitelik Değerini Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 48ad3c0ab079012793fd9eea89d52fc3a7b1698f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397810"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir özniteliğin değerini alma (LINQ to XML) (Visual Basic)
Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir. İki ana yol vardır: bir <xref:System.Xml.Linq.XAttribute> türü istenen türe çevirebilirsiniz; açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür. Alternatif olarak, özelliğini de kullanabilirsiniz <xref:System.Xml.Linq.XAttribute.Value%2A> . Ancak, atama genellikle daha iyi bir yaklaşımdır. Özniteliğini null yapılabilir bir değer türüne ayarlarsanız, kod, var olabilen veya var olabilen bir özniteliğin değeri alınırken yazmak daha basittir. Bu tekniğin örnekleri için bkz. [nasıl yapılır: bir öğenin değerini alma (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Visual Basic, bir özniteliğin değerini almak için tümleşik öznitelik özelliğini kullanabilirsiniz.  
  
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
 Visual Basic, bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanabilirsiniz. Ayrıca, var olmayan bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanırsanız, öznitelik oluşturulur.  
  
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
 Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
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
  
```console  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
