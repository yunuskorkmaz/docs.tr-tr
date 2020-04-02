---
title: 'Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 8168c89a6edecd5f7e33a710c9a89c92a6f82005
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588238"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="04a5a-102">Nasıl Yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="04a5a-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="04a5a-103">Bu örnek, bir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> kaynak diziye özel bir toplama işlevi uygulamak için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04a5a-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="04a5a-104">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="04a5a-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="04a5a-105">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="04a5a-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a5a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="04a5a-106">Example</span></span>  
 <span data-ttu-id="04a5a-107">Aşağıdaki örnek, bir tamsayı dizisinin standart sapını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="04a5a-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="04a5a-108">Bu örnek, PLINQ'ye özgü Toplam standart sorgu işlecinin aşırı yüklenmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="04a5a-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="04a5a-109">Bu aşırı yük, <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak fazladan yük alır.</span><span class="sxs-lookup"><span data-stu-id="04a5a-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="04a5a-110">Bu temsilci, toplanan sonuçlar üzerinde son hesaplamayı gerçekleştirmeden önce tüm iş parçacıklarının sonuçlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="04a5a-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="04a5a-111">Bu örnekte, tüm iş parçacıklarının toplamlarını bir araya getiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="04a5a-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="04a5a-112">Lambda ifade gövdesi tek bir ifadeden oluşuyorsa, <xref:System.Func%602?displayProperty=nameWithType> temsilcinin dönüş değeri ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="04a5a-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a5a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a5a-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="04a5a-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="04a5a-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
