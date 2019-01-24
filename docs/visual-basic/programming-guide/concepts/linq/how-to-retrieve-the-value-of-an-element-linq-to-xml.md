---
title: 'Nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: 710b5d3e9c636c832d52206921f21c8141cf4319
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671531"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (Visual Basic)
Bu konuda, öğelerin değerini alma gösterilmektedir. Bunu yapmak için iki ana yolu vardır. Dönüştürülecek bir yolu olan bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> istenen türe. Açık dönüştürme işleci öğe veya öznitelik içeriğini belirtilen türe dönüştürür ve değişkeninize atar. Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> özelliği.  
  
 Visual Basic ile en iyi yaklaşımdır <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Bir öğenin değerini almak için yalnızca cast <xref:System.Xml.Linq.XElement> istenen türünüz için nesne. Her zaman bir dize için bir öğe gibi çevirebilirsiniz:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Ayrıca dize dışındaki türler için öğeleri çevirebilirsiniz. Bir tamsayı içeren bir öğe varsa, örneğin, kendisine çevirebilirsiniz `int`aşağıdaki kodda gösterildiği gibi:  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Aşağıdaki veri türleri için açık tür dönüştürme işleçleri sağlar: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, ve `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aynı atama işleçleri sağlar <xref:System.Xml.Linq.XAttribute> nesneleri.  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz <xref:System.Xml.Linq.XElement.Value%2A> özelliği, bir öğenin içeriğini almak için:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Bazen varolduğundan emin değilseniz olsa bile, bir öğenin değeri alınmaya çalışıldı. Bu durumda, atadığınızda Integer öğesi null yapılabilir bir tür (ya da `string` veya boş değer atanabilir türleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), öğe atanmış mevcut değilse değişkeni ayarlamanız yeterlidir `Nothing`. Aşağıdaki kodu öğesi olabilir ya da mevcut, atama kullanımı çok daha kolay olduğunu gösteriyor <xref:System.Xml.Linq.XElement.Value%2A> özelliği.  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Genel olarak, öğeleri ve özniteliklerinin içeriğini almak için atama kullanırken daha basit bir kod yazabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
