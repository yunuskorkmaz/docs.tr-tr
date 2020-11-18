---
title: 'Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: d04f90e9c763c8ddba5ba07b650ffb878869ff3a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825474"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="fdc66-102">Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="fdc66-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="fdc66-103">Bu örnek, <xref:System.Linq.ParallelEnumerable.Aggregate%2A> bir kaynak dizisine özel toplama işlevi uygulamak için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc66-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fdc66-104">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc66-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="fdc66-105">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="fdc66-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdc66-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdc66-106">Example</span></span>  
 <span data-ttu-id="fdc66-107">Aşağıdaki örnek, bir tamsayı dizisinin standart sapmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="fdc66-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="fdc66-108">Bu örnek, PLıNQ için benzersiz olan toplam standart sorgu işlecinin aşırı yüklemesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdc66-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="fdc66-109">Bu aşırı yükleme <xref:System.Func%603?displayProperty=nameWithType> , üçüncü giriş parametresi olarak ek sürer.</span><span class="sxs-lookup"><span data-stu-id="fdc66-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="fdc66-110">Bu temsilci, toplanan sonuçlarda nihai hesaplamayı gerçekleştirmeden önce tüm iş parçacıklarından sonuçları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="fdc66-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="fdc66-111">Bu örnekte, tüm iş parçacıklarından toplamları toplayın.</span><span class="sxs-lookup"><span data-stu-id="fdc66-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="fdc66-112">Lambda ifadesi gövdesi tek bir ifadeden oluşuyorsa, temsilcinin dönüş değeri <xref:System.Func%602?displayProperty=nameWithType> ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="fdc66-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc66-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc66-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="fdc66-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="fdc66-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
