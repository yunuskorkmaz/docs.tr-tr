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
ms.openlocfilehash: 03bbb9b7cf33eda1cc479759740e6c5325f635fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608768"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="1a2f7-102">Nasıl yapılır: Özel Bir PLINQ Toplama İşlevi Yazma</span><span class="sxs-lookup"><span data-stu-id="1a2f7-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="1a2f7-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.Aggregate%2A> yöntemi bir kaynak dizisi için bir özel toplama işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1a2f7-104">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1a2f7-105">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1a2f7-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a2f7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a2f7-106">Example</span></span>  
 <span data-ttu-id="1a2f7-107">Aşağıdaki örnek, tamsayı bir dizi standart sapmayı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="1a2f7-108">Bu örnekte, bir PLINQ için benzersiz olan toplama standart sorgu işleci aşırı yüklemesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="1a2f7-109">Bu aşırı ek alan <xref:System.Func%603?displayProperty=nameWithType> üçüncü giriş parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="1a2f7-110">Toplu sonuçları son hesaplama gerçekleştirmeden önce bu temsilci tüm iş parçacıklarının sonuçları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="1a2f7-111">Bu örnekte biz birlikte tüm iş parçacıklarından SUM'ları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="1a2f7-112">Bir lambda ifadesi gövdesi, dönüş değeri gibi tek bir ifade oluşuyorsa unutmayın <xref:System.Func%602?displayProperty=nameWithType> ifadenin değerini temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2f7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a2f7-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="1a2f7-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1a2f7-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
