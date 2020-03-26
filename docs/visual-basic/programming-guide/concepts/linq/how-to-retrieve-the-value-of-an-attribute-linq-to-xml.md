---
title: 'Nasıl Yapılır: Bir Özniteliğin Değerini Alın (LINQ- XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248953"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Nasıl Yapılır: Bir Özniteliğin Değerini (LINQ'dan XML'e) (Visual Basic) alın
Bu konu, özniteliklerin değerini nasıl elde edilebildiğini gösterir. İki ana yolu vardır: İstediğiniz türe bir <xref:System.Xml.Linq.XAttribute> döküm yapabilirsiniz; açık dönüştürme işleci daha sonra öğenin içeriğini veya belirtilen türe atnitelik dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği kullanabilirsiniz. Ancak, döküm genellikle daha iyi bir yaklaşımdır. Özniteliği boşkullanılabilir bir değer türüne atarsanız, var olabilir veya olmayabilir bir öznitelik değerini alırken kod yazmak daha kolaydır. Bu teknik örnekleri için [bkz: Bir Öğenin Değerini (LINQ-XML) (Visual Basic) alın.](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, bir özniteliğin değerini almak için tümleşik öznitelik özelliğini kullanabilirsiniz.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanabilirsiniz. Ayrıca, var olmayan bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliğini kullanırsanız, öznitelik oluşturulur.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özniteliğin ad alanında olduğu bir özniteliğin değerini nasıl alınacağını gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
