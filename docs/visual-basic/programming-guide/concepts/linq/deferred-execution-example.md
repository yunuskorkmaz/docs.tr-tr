---
title: Ertelenmiş yürütme örneği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6d1f66cbe246b609f634989625688965dd4e5c93
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351806"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="8fd2a-102">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fd2a-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="8fd2a-103">Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fd2a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fd2a-104">Example</span></span>  
 <span data-ttu-id="8fd2a-105">Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="8fd2a-106">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-106">The example declares an array of three strings.</span></span> <span data-ttu-id="8fd2a-107">Daha sonra `ConvertCollectionToUpperCase` tarafından döndürülen koleksiyon üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="8fd2a-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8fd2a-108">This example produces the following output:</span></span>  
  
```console  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="8fd2a-109">@No__t-0 tarafından döndürülen koleksiyon üzerinden yineleme yaparken, her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="8fd2a-110">Döndürülen koleksiyondaki her öğe, `Main` ' deki `foreach` döngüsünde işlenmeden önce tüm dizeler dizisinin büyük harfe dönüştürülmediğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd2a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fd2a-111">See also</span></span>

- [<span data-ttu-id="8fd2a-112">Öğretici: Ertelenmiş yürütme (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="8fd2a-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
