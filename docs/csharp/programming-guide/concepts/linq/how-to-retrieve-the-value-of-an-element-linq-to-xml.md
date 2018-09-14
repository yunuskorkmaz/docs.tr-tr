---
title: 'Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)'
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 7537c111e7d869f8a3e2458706864960820f9764
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609716"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)
Bu konuda, öğelerin değerini alma gösterilmektedir. Bunu yapmak için iki ana yolu vardır. Dönüştürülecek bir yolu olan bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> istenen türe. Açık dönüştürme işleci öğe veya öznitelik içeriğini belirtilen türe dönüştürür ve değişkeninize atar. Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> özelliği.  
  
 C# ile ancak atama genellikle daha iyi bir yaklaşımdır. Cast öğesi veya özniteliği için boş değer atanabilir bir tür, ne zaman yazmak daha basit kodudur var olmayabilir veya değeri bir öğenin (veya öznitelik) alma. Bu konu Son örnekte bu gösterir. Ancak aracılığıyla mümkün olduğunca atama, öğenin içeriğini ayarlanamıyor <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Bir öğenin değerini almak için yalnızca cast <xref:System.Xml.Linq.XElement> istenen türünüz için nesne. Her zaman bir dize için bir öğe gibi çevirebilirsiniz:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Ayrıca dize dışındaki türler için öğeleri çevirebilirsiniz. Bir tamsayı içeren bir öğe varsa, örneğin, kendisine çevirebilirsiniz `int`aşağıdaki kodda gösterildiği gibi:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Aşağıdaki veri türleri için açık tür dönüştürme işleçleri sağlar: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, ve `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aynı atama işleçleri sağlar <xref:System.Xml.Linq.XAttribute> nesneleri.  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz <xref:System.Xml.Linq.XElement.Value%2A> özelliği, bir öğenin içeriğini almak için:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Örnek  
 Bazen varolduğundan emin değilseniz olsa bile, bir öğenin değeri alınmaya çalışıldı. Bu durumda, atadığınızda Integer öğesi null yapılabilir bir tür (ya da `string` veya boş değer atanabilir türleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), öğe atanmış mevcut değilse değişkeni ayarlamanız yeterlidir `null`. Aşağıdaki kodu öğesi olabilir ya da mevcut, atama kullanımı çok daha kolay olduğunu gösteriyor <xref:System.Xml.Linq.XElement.Value%2A> özelliği.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
