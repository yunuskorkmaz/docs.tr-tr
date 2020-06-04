---
title: 'Nasıl yapılır: Öğe Değerini Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b8ff44416f0fbb590119af7e11714e449185d977
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397797"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir öğenin değerini alma (LINQ to XML) (Visual Basic)
Bu konu, öğelerin değerinin nasıl alınacağını gösterir. Bunu iki ana şekilde yapabilirsiniz. Tek yönlü bir <xref:System.Xml.Linq.XElement> veya öğesini <xref:System.Xml.Linq.XAttribute> istenen türe atama yöntemidir. Daha sonra açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür ve değişkenine atar. Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliğini veya özelliğini de kullanabilirsiniz <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> .  
  
 Visual Basic, en iyi yaklaşım <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği kullanmaktır.  
  
## <a name="example"></a>Örnek  
 Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atamalısınız. Bir öğeyi aşağıdaki gibi her zaman bir dizeye çevirebilirsiniz:  
  
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
 Ayrıca, öğeleri dize dışındaki türlere de çevirebilirsiniz. Örneğin, bir tamsayı içeren bir öğeye sahipseniz, `int` aşağıdaki kodda gösterildiği gibi, öğesini öğesine çevirebilirsiniz:  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Şu veri türleri için açık atama işleçleri sağlar: `string` , `bool` ,, `bool?` `int` , `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,, ve  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nesneler için aynı atama işleçlerini sağlar <xref:System.Xml.Linq.XAttribute> .  
  
## <a name="example"></a>Örnek  
 <xref:System.Xml.Linq.XElement.Value%2A>Bir öğenin içeriğini almak için özelliğini kullanabilirsiniz:  
  
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
 Bazen, var olmadığından emin olmasanız da bir öğenin değerini almaya çalışırsınız. Bu durumda, bulunan öğeyi null yapılabilir bir türe atadığınızda ( `string` .NET Framework), öğe yoksa, atanan değişken yalnızca ' a ayarlanır `Nothing` . Aşağıdaki kod, öğe ne zaman olabileceği veya mevcut olmadığında, özelliği kullanmak için, atama kullanmanın daha kolay olduğunu gösterir <xref:System.Xml.Linq.XElement.Value%2A> .  
  
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
  
 Genel olarak, öğelerin ve özniteliklerin içeriğini almak için atama kullanırken daha basit bir kod yazabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
