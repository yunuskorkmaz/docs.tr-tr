---
title: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)
description: Bu C# örneği, bir düğümden hemen önce gelen eşdüzey öğeyi bulmak için XPath 'i LINQ to XML karşılaştırır.
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: eaee7f1205ce0d0b2a9c2c41d96ba532573a1384
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105197"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)
Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz. XPath 'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bu, daha ilginç karşılaştırmalardan biridir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu, <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen koleksiyondaki son düğümü bulmak için işlecini kullanır <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> . Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.  
  
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
