---
title: Hemen önceki kardeş (XPath-LINQ - XML) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141008"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Hemen önceki kardeş (XPath-LINQ - XML) (C#) nasıl bulabilirim?
Bazen bir düğüm için hemen önceki kardeş bulmak istiyorum. XPath'te önceki kardeş eksenler için konumsal yüklemlerin semantikindeki farktan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dolayı, bu daha ilginç karşılaştırmalardan biridir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu <xref:System.Linq.Enumerable.Last%2A> tarafından <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>döndürülen koleksiyondaki son düğümü bulmak için işleci kullanır. Bunun aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değeri olan bir yüklem kullanır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
<Child3 />  
```  
