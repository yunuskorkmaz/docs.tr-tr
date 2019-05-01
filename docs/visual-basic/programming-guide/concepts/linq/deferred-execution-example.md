---
title: Ertelenmiş yürütme örneği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 29f118b3e6d49840b94277f17858f1339f2fb08c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977636"
---
# <a name="deferred-execution-example-visual-basic"></a>Ertelenmiş yürütme örneği (Visual Basic)
Bu konu nasıl ertelenmiş yürütme gösterir ve geç değerlendirme, LINQ to XML sorgularında yürütme etkiler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken, yürütme sırasını gösterir. Örneğin, üç dize dizisi bildirir. Bunun ardından tarafından döndürülen bir koleksiyonda gezinir `ConvertCollectionToUpperCase`.  
  
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
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Tarafından döndürülen koleksiyon üzerinden yineleme sırasında dikkat `ConvertCollectionToUpperCase`, her öğe kaynak string dizisinden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak string dizisinden alınır.  
  
 Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizi dizeleri büyük harfe dönüştürülmesi değil gördüğünüz `foreach` içinde döngü `Main`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
