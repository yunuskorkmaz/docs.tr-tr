---
title: İsteğe bağlı bir öğeye nasıl filtre yapılır (C#)
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: c9f844619cbb3d7a66ca66989baa900e0fd7bc2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141246"
---
# <a name="how-to-filter-on-an-optional-element-c"></a>İsteğe bağlı bir öğeye nasıl filtre yapılır (C#)
Bazen XML belgenizde var olduğundan emin değilseniz bile bir öğe için filtre yapmak istersiniz. Arama, belirli öğealt öğeye sahip değilse, bunun için filtre uygulayarak null bir başvuru özel durum tetiklemez, böylece yürütülmelidir. Aşağıdaki örnekte, `Child5` öğenin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> uzantı yöntemini kullanır.  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Projeksiyon İşlemleri (C#)](./projection-operations.md)
