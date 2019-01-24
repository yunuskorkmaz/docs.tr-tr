---
title: Ertelenmiş yürütme örneği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: e9247c89d46cc7705ef4297868739ba85d993eec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614178"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="bd22c-102">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd22c-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="bd22c-103">Bu konu nasıl ertelenmiş yürütme gösterir ve geç değerlendirme, LINQ to XML sorgularında yürütme etkiler.</span><span class="sxs-lookup"><span data-stu-id="bd22c-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd22c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd22c-104">Example</span></span>  
 <span data-ttu-id="bd22c-105">Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken, yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd22c-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="bd22c-106">Örneğin, üç dize dizisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd22c-106">The example declares an array of three strings.</span></span> <span data-ttu-id="bd22c-107">Bunun ardından tarafından döndürülen bir koleksiyonda gezinir `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="bd22c-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="bd22c-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bd22c-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="bd22c-109">Tarafından döndürülen koleksiyon üzerinden yineleme sırasında dikkat `ConvertCollectionToUpperCase`, her öğe kaynak string dizisinden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak string dizisinden alınır.</span><span class="sxs-lookup"><span data-stu-id="bd22c-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="bd22c-110">Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizi dizeleri büyük harfe dönüştürülmesi değil gördüğünüz `foreach` içinde döngü `Main`.</span><span class="sxs-lookup"><span data-stu-id="bd22c-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd22c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd22c-111">See also</span></span>
- [<span data-ttu-id="bd22c-112">Öğretici: Ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd22c-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
