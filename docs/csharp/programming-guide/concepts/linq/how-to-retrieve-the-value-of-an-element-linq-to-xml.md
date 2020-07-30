---
title: Bir öğenin değerini alma (LINQ to XML) (C#)
description: Öğelerin değerini alma hakkında bilgi edinin. Bkz. dize çevrim, tamsayı atama ve değer özelliği kullanma örnekleri.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301547"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Bir öğenin değerini alma (LINQ to XML) (C#)

Bu makale, öğelerin değerinin nasıl alınacağını gösterir. Değeri almanın iki ana yolu vardır:

- Bir <xref:System.Xml.Linq.XElement> veya öğesini <xref:System.Xml.Linq.XAttribute> istenen türe atayın. Daha sonra açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür ve değişkenine atar.

- <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>Veya özelliklerini kullanın <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> . Bu özellikleri kullanarak da değeri ayarlayabilirsiniz.

C# ile, atama genellikle daha iyi bir yaklaşımdır. Öğesi veya özniteliğini null atanabilir bir değer türüne ayarlarsanız, kod, var olabilen veya varolmayan bir öğenin (veya özniteliğin) değeri alınırken yazmak daha basittir. Bu makaledeki [Son örnekte](#element-might-not-exist-example) , öğenin mevcut olmadığı durumlarda atama daha basit olduğu gösterilmektedir. Ancak, özelliğini kullanarak bir öğenin içeriğini atama aracılığıyla ayarlayamazsınız <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> .  
  
## <a name="string-cast-example"></a>Dize atama örneği  
 Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atayın. Bir öğeyi şu şekilde bir dizeye çevirebilirsiniz:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Şu veri türleri için açık atama işleçleri sağlar: `string` , `bool` ,, `bool?` `int` , `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,, ve  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nesneler için aynı atama işleçlerini sağlar <xref:System.Xml.Linq.XAttribute> .  
  
## <a name="value-property-example"></a>Value özelliği örneği  
 <xref:System.Xml.Linq.XElement.Value%2A>Bir öğenin içeriğini almak için özelliğini kullanabilirsiniz:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>Öğe mevcut olmayabilir örnek
 Bazen, var olup olmadığından emin olmadığınız halde bir öğenin değerini almaya çalışırsınız. Bu durumda, başvurulan öğeyi null olabilen bir başvuru türüne veya null yapılabilir değer türüne atadığınızda, öğe yoksa atanan değişken olarak ayarlanır `null` . Aşağıdaki kod, öğe ne zaman olabileceği veya mevcut olmadığında, özelliği kullanmak için, atama kullanmanın daha kolay olduğunu gösterir <xref:System.Xml.Linq.XElement.Value%2A> .  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
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
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
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

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
