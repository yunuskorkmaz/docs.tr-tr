---
title: 'Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulun (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 00b74edd67df65522f9f95e7f48c66a9e17a937c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708486"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a>Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulun (C#)
Bazen bir düğüme önceki eşdüzeyi bulma istersiniz. XPath başlangıcı yerine sonundan önceki eşdüzey eksenleri için konumsal doğrulamaları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilgi çekici karşılaştırmalar biridir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullandığı <xref:System.Linq.Enumerable.Last%2A> son düğümü tarafından döndürülen bir koleksiyonda bulunacak işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerini bir koşul kullanır.  
  
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
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
