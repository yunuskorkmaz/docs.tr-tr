---
title: 'Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: f4e895e560d0fb11c128248e4f42d1d5124bc124
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma
İçinde bir ad alanı XML bir sorgu yazmak için kullanmanız gerekir <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri.  
  
 Visual Basic'te en yaygın genel ad alanı tanımlamak ve XML değişmez değerleri ve genel ad alanı kullanmak XML özellikleri kullanmak için bir yaklaşımdır. Genel varsayılan ad alanı, varsayılan olarak ad alanında XML değişmez değerleri öğelerinde; Bu durumda olacaktır tanımlayabilirsiniz. Alternatif olarak, genel ad alanı öneki tanımlamak ve XML değişmez değerleri ve XML özellikleri gerektiği gibi ön ekini kullanın. Formlarla diğer XML gibi her zaman varsayılan olarak hiçbir ad alanındaki öznitelikleridir.  
  
 Bu konudaki örnekler ilk kümesi varsayılan ad alanında bir XML ağacı oluşturulacağını gösterir. İkinci küme öneki bir ad alanındaki bir XML ağacı oluşturulacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Örnek  
 Visual Basic'te, ancak, bir ad alanı öneki ile kullanan bir XML ağaç sorguları yazma bir varsayılan ad alanı XML ağacında sorgulama oldukça farklıdır. Tipik olarak kullandığınız `Imports` ad alanı öneki almak için deyimi. XML ağaç yapısı oluştururken öğe ve öznitelik adları ön ekini kullanın. XML özellikleri kullanılarak bir XML ağacı sorgulanırken de ön ekini kullanın.  
  
 Aşağıdaki örnek, bir ad alanı öneki bulunduğu bir XML ağacı oluşturur. Ardından, öğe koleksiyonunu alır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
