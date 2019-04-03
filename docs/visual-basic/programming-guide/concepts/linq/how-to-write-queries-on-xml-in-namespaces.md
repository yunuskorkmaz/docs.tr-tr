---
title: 'Nasıl yapılır: (Visual Basic) ad alanlarında XML üzerinde sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 4efa1de254a0264752514c5ae6e601a66fa56f95
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833444"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Nasıl yapılır: (Visual Basic) ad alanlarında XML üzerinde sorgu yazma
Bir ad alanındaki XML üzerinde sorgu yazmak için kullanmalısınız <xref:System.Xml.Linq.XName> doğru ad alanı olan nesne.  
  
 Visual Basic'te, en yaygın bir genel ad alanı tanımlayın ve ardından XML sabit değerleri ve XML özellikleri, genel ad kullanmak yaklaşımdır. XML değişmez değerlerinde bir öğe ad varsayılan olarak, bu durumda olacaktır, bir genel varsayılan ad alanı tanımlayabilirsiniz. Alternatif olarak, genel bir ad alanı öneki ile tanımlayabilir ve ardından XML sabit değerleri ve XML özellikleri gerektiği gibi ön ekini kullanın. Formlarla diğer XML olarak, öznitelikleri her zaman varsayılan olarak hiçbir ad alanı olur.  
  
 Bu konudaki örnekler ilk kümesi, varsayılan ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir. İkinci küme, önekli ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur. Ardından, öğelerinin bir koleksiyonunu alır.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, ancak bir ad alanı öneki ile kullanan bir XML ağacının üzerinde sorgu yazma bir XML ağacı varsayılan ad alanı içinde sorgulamaktan oldukça farklıdır. Tipik olarak kullandığınız `Imports` ad alanı öneki ile içeri aktarma deyimi. XML ağacı oluştururken öğe ve öznitelik adları önekini kullanın. XML özelliklerini kullanarak bir XML ağacı sorgulanırken de ön ekini kullanın.  
  
 Aşağıdaki örnek, bir ad alanı öneki olan bir XML ağacı oluşturur. Ardından, öğelerinin bir koleksiyonunu alır.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
