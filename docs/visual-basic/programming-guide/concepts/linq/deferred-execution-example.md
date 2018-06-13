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
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="45737-102">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45737-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="45737-103">Geç değerlendirme, LINQ to XML sorgularını yürütme etkiler ve bu konuda nasıl ertelenmiş yürütme gösterir.</span><span class="sxs-lookup"><span data-stu-id="45737-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45737-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="45737-104">Example</span></span>  
 <span data-ttu-id="45737-105">Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45737-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="45737-106">Örnek üç bir dizeler dizisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="45737-106">The example declares an array of three strings.</span></span> <span data-ttu-id="45737-107">Ardından tarafından döndürülen koleksiyon üzerinden yineleme `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="45737-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="45737-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="45737-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="45737-109">Tarafından döndürülen koleksiyon üzerinden yineleme zaman fark `ConvertCollectionToUpperCase`, her öğe kaynak dize diziden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak dize diziden alınır.</span><span class="sxs-lookup"><span data-stu-id="45737-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="45737-110">Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizisini büyük harfe dönüştürülmez olduğunu görebilirsiniz `foreach` içinde döngü `Main`.</span><span class="sxs-lookup"><span data-stu-id="45737-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45737-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45737-111">See Also</span></span>  
 [<span data-ttu-id="45737-112">Öğretici: Ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45737-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
