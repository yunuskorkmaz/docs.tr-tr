---
title: 'Nasıl yapılır: hata ayıklama boş sorgu sonuç kümeleri (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 33dcfe9b0c0ad41353ca845ed4d8e21ff77292df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642980"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Nasıl yapılır: hata ayıklama boş sorgu sonuç kümeleri (Visual Basic)
XML ağaçları sorgulanırken en yaygın sorunları XML ağacında bir varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanındaki Geliştirici bazen sorgu yazdığını biridir.  
  
 Bu konudaki örnekler ilk kümesi, bir varsayılan ad alanı XML yüklenir ve yanlış sorgulanan tipik bir yolunu gösterir.  
  
 XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.  
  
 Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanındaki XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
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
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 Bu örnekte aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu XML oluşturulmasını gösterir.  
  
 Bildirme ve bir genel varsayılan ad alanı başlatmak için kullanılan çözümüdür. Bu, varsayılan ad alanını tüm XML özellikleri yerleştirir. Başka bir değişiklikler örneği düzgün çalışması için gereklidir.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
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
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 Bu örnekte aşağıdaki sonucu üretir:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel sorgu (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
