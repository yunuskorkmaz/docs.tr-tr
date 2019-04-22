---
title: 'Nasıl yapılır: (Visual Basic) Descendants yöntemini kullanarak tek bir alt öğeyi bulma'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 0a2574422f95ed4d2b82c33ee999b233d95ea398
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826463"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a>Nasıl yapılır: (Visual Basic) Descendants yöntemini kullanarak tek bir alt öğeyi bulma
Kullanabileceğiniz <xref:System.Xml.Linq.XContainer.Descendants%2A> adlı öğesi hızlı bir şekilde tek bir benzersiz bir şekilde bulmak için kod yazma eksen yöntemi. Belirli bir ada sahip belirli bir alt öğesi bulmak istediğinizde bu özellikle yararlı bir tekniktir. İstenen öğesine gitmek için kod yazabilirsiniz, ancak genellikle daha hızlı ve kolay kullanarak kod yazmak <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.First%2A> standart sorgu işleci.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
