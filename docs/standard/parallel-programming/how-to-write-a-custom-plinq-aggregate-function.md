---
title: "Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="aa253-102">Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="aa253-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="aa253-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> yöntemi bir özel toplama işlevi için kaynak sıradaki uygular.</span><span class="sxs-lookup"><span data-stu-id="aa253-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="aa253-104">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="aa253-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="aa253-105">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="aa253-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa253-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa253-106">Example</span></span>  
 <span data-ttu-id="aa253-107">Aşağıdaki örnek, tamsayı bir dizi standart sapmayı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aa253-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="aa253-108">Bu örnek bir aşırı yüklemesini PLINQ için benzersizdir toplama standart sorgu işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa253-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="aa253-109">Bu aşırı fazladan alır <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="aa253-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="aa253-110">Toplanan sonuçlarına son hesaplama gerçekleştirmeden önce bu temsilci tüm iş parçacıklarının gelen sonuçları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="aa253-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="aa253-111">Bu örnekte, biz birlikte tüm iş parçacıklarının SUM'ları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa253-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="aa253-112">Lambda ifadesi gövdesi tek bir ifade, dönüş değerini oluşuyorsa unutmayın <xref:System.Func%602?displayProperty=nameWithType> temsilci ifade değerdir.</span><span class="sxs-lookup"><span data-stu-id="aa253-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa253-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa253-113">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="aa253-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="aa253-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
