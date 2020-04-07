---
title: Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805824"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?

Bu makalede, öğelerin değerini almak için nasıl gösterir. Değeri elde etmenin iki ana yolu vardır:

- Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> bir istenilen türe döküm. Açık dönüştürme işleci daha sonra öğenin içeriğini dönüştürür veya belirtilen türe atfeder ve değişkeninize atar.

- Özellikleri <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> özelliklerini kullanın. Bu özellikleri kullanarak değeri de ayarlayabilirsiniz.

C# ile, döküm genellikle daha iyi bir yaklaşımdır. Öğeyi veya özniteliği boşalabilir bir değer türüne atarsanız, var olabilecek veya var olmayan bir öğenin (veya öznitelik) değerini alırken kod yazmak daha kolaydır. Bu makaledeki [son örnek,](#element-might-not-exist-example) öğenin var olmadığı durumlarda dökümün daha basit olduğunu göstermektedir. Ancak, bir öğenin içeriğini, özellik aracılığıyla olduğu <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> gibi, döküm yoluyla ayarlayamazsınız.  
  
## <a name="string-cast-example"></a>String döküm örneği  
 Bir öğenin değerini almak için <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atın. Bir öğeyi aşağıdaki gibi bir dize atabilirsiniz:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>İnteger döküm örneği  
 Ayrıca, dize dışındaki türlere öğeleri de atabilirsiniz. Örneğin, bir arameger içeren bir öğeniz varsa, aşağıdaki `int`kodda gösterildiği gibi bu öğeyi şu şekilde atabilirsiniz:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aşağıdaki veri türleri için açık `string`döküm `bool` `bool?`operatörleri `int` `int?`sağlar: `uint?` `long`, `long?` `ulong`, `ulong?` `float`, `float?` `uint` `double`, `double?` `decimal`, `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`, , `GUID`, `GUID?`, , , , , , , , , , , ,  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nesneler için <xref:System.Xml.Linq.XAttribute> aynı döküm işleçleri sağlar.  
  
## <a name="value-property-example"></a>Değer özelliği örneği  
 Bir öğenin <xref:System.Xml.Linq.XElement.Value%2A> içeriğini almak için özelliği kullanabilirsiniz:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>Öğe örnek olmayabilir
 Bazen var olup olmadığından emin olmamanız aletin değerini almaya çalışırsınız. Bu durumda, döküm öğeyi nullable başvuru türüne veya nullable değer türüne atadığınızda, öğe yoksa, `null`atanan değişken . Aşağıdaki kod, öğe var olabilir veya olmayabilir, <xref:System.Xml.Linq.XElement.Value%2A> özelliği kullanmak için daha döküm kullanmak daha kolay olduğunu gösterir.  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
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
  
 Genel olarak, öğelerin ve özniteliklerin içeriğini almak için döküm kullanırken daha basit kod yazabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
