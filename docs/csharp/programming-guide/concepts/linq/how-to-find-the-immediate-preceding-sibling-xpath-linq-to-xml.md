---
title: 'Nasıl yapılır: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: bc0a3250cf1f56ebf9a367f6472be8f3230cee5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253626"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Nasıl yapılır: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)
Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz. XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle bu, daha ilginç karşılaştırmalardan biridir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu, tarafından <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>döndürülen koleksiyondaki son <xref:System.Linq.Enumerable.Last%2A> düğümü bulmak için işlecini kullanır. Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
<Child3 />  
```  
