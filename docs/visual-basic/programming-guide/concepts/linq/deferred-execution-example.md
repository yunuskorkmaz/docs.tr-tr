---
title: Ertelenmiş Yürütme Örneği
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6ab8f6434bb24b7a66ca4afd1d082911481671f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354235"
---
# <a name="deferred-execution-example-visual-basic"></a>Ertelenmiş yürütme örneği (Visual Basic)

Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir. Örnek, üç dizeden oluşan bir dizi bildirir. Daha sonra `ConvertCollectionToUpperCase`tarafından döndürülen koleksiyon üzerinden yinelenir.

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

`ConvertCollectionToUpperCase`tarafından döndürülen koleksiyon üzerinden yineleme yaparken, her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.

Döndürülen koleksiyondaki her öğe, `Main``foreach` döngüsünde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
