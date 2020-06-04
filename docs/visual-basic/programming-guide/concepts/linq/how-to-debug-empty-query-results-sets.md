---
title: 'Nasıl yapılır: Boş Sorgu Sonucu Kümelerinin Hatalarını Ayıklama'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: b2059ccd4638d2fb77c524773cb4bd50f721b5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398044"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Nasıl yapılır: boş sorgu sonuçları kümelerinde hata ayıklama (Visual Basic)

XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.

Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği ve yanlış sorgulandığı tipik bir yöntemi gösterir.

İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.

Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).

## <a name="example"></a>Örnek

Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.

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

Bu örnek aşağıdaki sonucu üretir:

```console
Result set follows:
End of result set
```

## <a name="example"></a>Örnek

Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.

Çözüm, genel bir varsayılan ad alanını bildirmek ve başlatmak. Bu, tüm XML özelliklerini varsayılan ad alanına koyar. Doğru çalışması için örnek için başka bir değişiklik yapmanız gerekmez.

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

Bu örnek aşağıdaki sonucu üretir:

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
