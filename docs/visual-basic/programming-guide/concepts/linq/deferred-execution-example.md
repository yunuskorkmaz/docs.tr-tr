---
title: Ertelenmiş yürütme örneği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642135"
---
# <a name="deferred-execution-example-visual-basic"></a>Ertelenmiş yürütme örneği (Visual Basic)
Geç değerlendirme, LINQ to XML sorgularını yürütme etkiler ve bu konuda nasıl ertelenmiş yürütme gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken yürütme sırasını gösterir. Örnek üç bir dizeler dizisi bildirir. Ardından tarafından döndürülen koleksiyon üzerinden yineleme `ConvertCollectionToUpperCase`.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Tarafından döndürülen koleksiyon üzerinden yineleme zaman fark `ConvertCollectionToUpperCase`, her öğe kaynak dize diziden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak dize diziden alınır.  
  
 Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizisini büyük harfe dönüştürülmez olduğunu görebilirsiniz `foreach` içinde döngü `Main`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
