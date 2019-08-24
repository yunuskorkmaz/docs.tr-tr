---
title: 'Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09e128c98b61ecc4ac673d8c9911f4bac476d521
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988431"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="a2449-102">Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="a2449-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="a2449-103">Bu örnek, <xref:System.Linq.ParallelEnumerable.Aggregate%2A> bir kaynak dizisine özel toplama işlevi uygulamak için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2449-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a2449-104">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a2449-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="a2449-105">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="a2449-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2449-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2449-106">Example</span></span>  
 <span data-ttu-id="a2449-107">Aşağıdaki örnek, bir tamsayı dizisinin standart sapmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="a2449-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="a2449-108">Bu örnek, PLıNQ için benzersiz olan toplam standart sorgu işlecinin aşırı yüklemesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2449-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="a2449-109">Bu aşırı yükleme, üçüncü <xref:System.Func%603?displayProperty=nameWithType> giriş parametresi olarak ek sürer.</span><span class="sxs-lookup"><span data-stu-id="a2449-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="a2449-110">Bu temsilci, toplanan sonuçlarda nihai hesaplamayı gerçekleştirmeden önce tüm iş parçacıklarından sonuçları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2449-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="a2449-111">Bu örnekte, tüm iş parçacıklarından toplamları toplayın.</span><span class="sxs-lookup"><span data-stu-id="a2449-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="a2449-112">Lambda ifadesi gövdesi tek bir ifadeden oluşuyorsa, <xref:System.Func%602?displayProperty=nameWithType> temsilcinin dönüş değeri ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="a2449-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2449-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2449-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="a2449-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a2449-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
