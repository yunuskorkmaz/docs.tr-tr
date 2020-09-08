---
title: Bir öğenin değerini alma-LINQ to XML
description: 'Bir öğenin veya özniteliğin değerini almanın iki ana yolunu öğrenin: istenen türe atama ya da XElement. Value ve XAttribute. Value özelliklerini kullanma.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 010af5db9ec991bfe0345c93def3241150aa15e2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553645"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml"></a>Öğe değerini alma (LINQ to XML)

Bu makale, öğelerin değerinin nasıl alınacağını gösterir. Değeri almanın iki ana yolu vardır:

- Bir <xref:System.Xml.Linq.XElement> veya öğesini <xref:System.Xml.Linq.XAttribute> istenen türe atayın. Daha sonra açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür ve değişkenine atar.

- <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>Veya özelliklerini kullanın <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> . Bu özellikleri kullanarak da değeri ayarlayabilirsiniz.

C# ile, atama genellikle daha iyi bir yaklaşımdır. Öğesi veya özniteliğini null yapılabilir bir değer türüne ayarlarsanız, var olmayan bir öğenin (veya özniteliğin) değeri alınırken yazma daha basittir. Bu makaledeki Son örnekte bu gösterilmektedir. Ancak, özelliğini kullanarak bir öğenin içeriğini atama aracılığıyla ayarlayamazsınız <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> .

Visual Basic, özelliği kullanmak daha iyi bir yaklaşımdır <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> .

## <a name="string-cast-example"></a>Dize atama örneği  

Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atayın. Bir öğeyi şu şekilde bir dizeye çevirebilirsiniz:

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (string)e);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="integer-cast-example"></a>Tamsayı atama örneği  

Ayrıca, öğeleri dize dışındaki türlere de çevirebilirsiniz. Örneğin, bir tamsayı içeren bir öğeye sahipseniz, `int` aşağıdaki kodda gösterildiği gibi, öğesini öğesine çevirebilirsiniz:  

```csharp
XElement e = new XElement("Age", "44");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (int)e);
```

```vb
Dim e As XElement = <Age>44</Age>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & CInt(e))
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
<Age>44</Age>
Value of e:44
```

LINQ to XML, aşağıdaki veri türleri için açık atama işleçleri sağlar: `string` , `bool` , `bool?` , `int` , `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,

LINQ to XML nesneler için aynı atama işleçlerini sağlar <xref:System.Xml.Linq.XAttribute> .

## <a name="value-property-example"></a>Value özelliği örneği

<xref:System.Xml.Linq.XElement.Value%2A>Bir öğenin içeriğini almak için özelliğini kullanabilirsiniz:

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + e.Value);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="element-might-not-exist-example"></a>Öğe mevcut olmayabilir örnek

Bazen, var olup olmadığından emin olmadığınız halde bir öğenin değerini almaya çalışırsınız. Bu durumda, başvurulan öğeyi null olabilen bir başvuru türüne veya null atanabilir değer türüne atadığınızda, öğe yoksa atanan değişken `null` (C#) veya `nothing` (Visual Basic) olarak ayarlanır. Aşağıdaki kod, öğe mevcut olmadığında, özelliği kullanmak için ' nin kullanımını daha kolay bir şekilde gösterir <xref:System.Xml.Linq.XElement.Value%2A> .

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "child 1 content"),
    new XElement("Child2", "2")
);

// The following assignments show why it's easier to use
// casting when the element might or might not exist.

string c1 = (string)root.Element("Child1");
Console.WriteLine("c1:{0}", c1 == null ? "element doesn't exist" : c1);

int? c2 = (int?)root.Element("Child2");
Console.WriteLine("c2:{0}", c2 == null ? "element doesn't exist" : c2.ToString());

string c3 = (string)root.Element("Child3");
Console.WriteLine("c3:{0}", c3 == null ? "element doesn't exist" : c3);

int? c4 = (int?)root.Element("Child4");
Console.WriteLine("c4:{0}", c4 == null ? "element doesn't exist" : c4.ToString());

Console.WriteLine();

// The following assignments show the required code when using
// the Value property when the element might or might not exist.
// Notice that this is more difficult than the casting approach.

XElement e1 = root.Element("Child1");
string v1;
if (e1 == null)
    v1 = null;
else
    v1 = e1.Value;
Console.WriteLine("v1:{0}", v1 == null ? "element doesn't exist" : v1);

XElement e2 = root.Element("Child2");
int? v2;
if (e2 == null)
    v2 = null;
else
    v2 = Int32.Parse(e2.Value);
Console.WriteLine("v2:{0}", v2 == null ? "element doesn't exist" : v2.ToString());

XElement e3 = root.Element("Child3");
string v3;
if (e3 == null)
    v3 = null;
else
    v3 = e3.Value;
Console.WriteLine("v3:{0}", v3 == null ? "element doesn't exist" : v3);

XElement e4 = root.Element("Child4");
int? v4;
if (e4 == null)
    v4 = null;
else
    v4 = Int32.Parse(e4.Value);
Console.WriteLine("v4:{0}", v4 == null ? "element doesn't exist" : v4.ToString());
```

```vb
Dim root As XElement = <Root>
                           <Child1>child 1 content</Child1>
                           <Child2>2</Child2>
                       </Root>

' The following assignments show why it's easier to use
' casting when the element might or might not exist.

Dim c1 As String = CStr(root.Element("Child1"))
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element doesn't exist", c1))

Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element doesn't exist", c2.ToString()))

Dim c3 As String = CStr(root.Element("Child3"))
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element doesn't exist", c3))

Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element doesn't exist", c4.ToString()))

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
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element doesn't exist", v1))

Dim e2 As XElement = root.Element("Child2")
Dim v2 As Nullable(Of Integer)
If (e2 Is Nothing) Then
    v2 = Nothing
Else
    v2 = e2.Value
End If
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element doesn't exist", v2))

Dim e3 As XElement = root.Element("Child3")
Dim v3 As String
If (e3 Is Nothing) Then
    v3 = Nothing
Else
    v3 = e3.Value
End If
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element doesn't exist", v3))

Dim e4 As XElement = root.Element("Child4")
Dim v4 As Nullable(Of Integer)
If (e4 Is Nothing) Then
    v4 = Nothing
Else
    v4 = e4.Value
End If
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element doesn't exist", v4))
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
c1:child 1 content
c2:2
c3:element doesn't exist
c4:element doesn't exist

v1:child 1 content
v2:2
v3:element doesn't exist
v4:element doesn't exist
```

Genel olarak, öğelerin ve özniteliklerin içeriğini almak için, atama yaparak daha basit bir kod yazabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
