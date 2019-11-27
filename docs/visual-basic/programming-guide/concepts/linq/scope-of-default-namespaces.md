---
title: Varsayılan Ad Alanlarının Kapsamı
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343653"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Visual Basic varsayılan ad alanlarının kapsamı
XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir. Varsayılan bir ad alanında olan XML varsa, sorguda kullanılacak nitelikli bir ad oluşturmak için bir <xref:System.Xml.Linq.XNamespace> değişkeni bildirmeniz ve yerel adla birleştirmeniz gerekir.  
  
 XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.  
  
 Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği, ancak yanlış sorgulandığı tipik bir yöntemi gösterir.  
  
 İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.  
  
### <a name="code"></a>Kod  
  
```vb  
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
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.  
  
 Yukarıdaki yanlış kodlanmış örneğin aksine, Visual Basic kullanırken doğru yaklaşım genel bir varsayılan ad alanını bildirmek ve başlatmak olur. Bu, tüm XML özelliklerini varsayılan ad alanına koyar. Doğru çalışması için örnek için başka bir değişiklik yapmanız gerekmez.  
  
### <a name="code"></a>Kod  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki sonucu üretir:  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
