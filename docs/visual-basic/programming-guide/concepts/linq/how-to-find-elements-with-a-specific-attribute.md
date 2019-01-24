---
title: 'Nasıl yapılır: (XPath-LINQ to XML) belirli bir özniteliğe sahip öğeleri bulma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 0efc0d6cebce760d90213d5149ca729a7b04663e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654431"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: (XPath-LINQ to XML) belirli bir özniteliğe sahip öğeleri bulma (Visual Basic)
Bazen belirli bir özniteliği olan tüm öğeleri bulmak istediğiniz. Özniteliğin içeriği hakkında endişe değildir. Bunun yerine, seçilecek öznitelik varlığı üzerinde temel istediğiniz.  
  
 XPath ifadesidir:  
  
 `./*[@Select]`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu olan öğeleri seçer `Select` özniteliği.  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
If list1.Count() = list2.Count() And _  
    list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to XML için XPath kullanıcıları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
