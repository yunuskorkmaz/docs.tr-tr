---
title: 'Nasıl Yapılır: Bir Öğenin Değerini Alın (LINQ - XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b1a61091dc59b403c5d967609e8870492c24347f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248940"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Nasıl Yapılır: Bir Öğenin Değerini Alın (LINQ - XML) (Visual Basic)
Bu konu, öğelerin değerini nasıl elde edilebildiğini gösterir. Bunu yapmanın iki ana yolu vardır. Bir yolu istenilen <xref:System.Xml.Linq.XElement> türe <xref:System.Xml.Linq.XAttribute> bir veya bir döküm etmektir. Açık dönüştürme işleci daha sonra öğenin içeriğini dönüştürür veya belirtilen türe atfeder ve değişkeninize atar. Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> mülkü kullanabilirsiniz.  
  
 Visual Basic ile en iyi yaklaşım <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği kullanmaktır.  
  
## <a name="example"></a>Örnek  
 Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe dökmeniz yalnızca Bir öğeyi her zaman aşağıdaki gibi bir dize atabilirsiniz:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Ayrıca, dize dışındaki türlere öğeleri de atabilirsiniz. Örneğin, bir arameger içeren bir öğeniz varsa, aşağıdaki `int`kodda gösterildiği gibi bu öğeyi şu şekilde atabilirsiniz:  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aşağıdaki veri türleri için açık `string`döküm `bool` `bool?`operatörleri `int` `int?`sağlar: `uint?` `long`, `long?` `ulong`, `ulong?` `float`, `float?` `uint` `double`, `double?` `decimal`, `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`, , `GUID`, `GUID?`, , , , , , , , , , , ,  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nesneler için <xref:System.Xml.Linq.XAttribute> aynı döküm işleçleri sağlar.  
  
## <a name="example"></a>Örnek  
 Bir öğenin <xref:System.Xml.Linq.XElement.Value%2A> içeriğini almak için özelliği kullanabilirsiniz:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Bazen var olduğundan emin olsanız bile bir öğenin değerini almaya çalışırsınız. Bu durumda, döküm öğeyi geçersiz bir türe (.NET Çerçevesi'ndeki nullable değer türlerinden birine `string` veya biri) atadığınızda, öğe `Nothing`yoksa atanan değişken sadece . Aşağıdaki kod, öğe var olabilir veya olmayabilir, <xref:System.Xml.Linq.XElement.Value%2A> özelliği kullanmak için daha döküm kullanmak daha kolay olduğunu gösterir.  
  
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
  
```console  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Genel olarak, öğelerin ve özniteliklerin içeriğini almak için döküm kullanırken daha basit kod yazabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
