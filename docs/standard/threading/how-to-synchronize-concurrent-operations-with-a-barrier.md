---
title: 'Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194500"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="e5c78-102">Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme</span><span class="sxs-lookup"><span data-stu-id="e5c78-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="e5c78-103">Aşağıdaki örnek, eş zamanlı görevleri ile eşitlemek gösterilmiştir bir <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="e5c78-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c78-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5c78-104">Example</span></span>  
 <span data-ttu-id="e5c78-105">Aşağıdaki program amacı kaç yineleme (veya aşamaları) sayısı için her bulunacak iki iş parçacığı için çözümü kendi yarısında aynı aşamaya sözcük sırasını yeniden ayarlaması randomizing bir algoritma kullanarak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5c78-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="e5c78-106">Her iş parçacığı, sözcükleri karışık sonra engeli sonrası aşamasını işlemi doğru sözcük sırada işlendikten tam bir cümle görmek için iki sonucu karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e5c78-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="e5c78-107">A <xref:System.Threading.Barrier> tüm görevler engel ulaşana kadar devam etmesini bir paralel işlemin içinde tek tek görevler engelleyen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e5c78-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="e5c78-108">Bu aşamada paralel işlem gerçekleşir ve her aşamada görevler arasında eşitleme gerektirir yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e5c78-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="e5c78-109">Bu örnekte, işlemi için iki aşaması vardır.</span><span class="sxs-lookup"><span data-stu-id="e5c78-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="e5c78-110">İlk aşamada, her görev kendi bölümü arabellek verilerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="e5c78-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="e5c78-111">Her görev kendi bölümü doldurma tamamlandığında, görev, devam etmeye hazır engel ve bekler bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5c78-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="e5c78-112">Tüm Görevler engel sinyal kullanıcılar, engeli ve ikinci aşaması başlar.</span><span class="sxs-lookup"><span data-stu-id="e5c78-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="e5c78-113">İkinci aşama, her görev, bu noktada oluşturulan tüm veri erişimi olmasını gerektirdiğinden engel gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5c78-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="e5c78-114">Engel ilk görevleri tamamlamak için henüz diğer görevler tarafından doldurulmuştur olmayan arabellekler okunacak deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="e5c78-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="e5c78-115">Bu aşamada herhangi bir sayıda eşitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5c78-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c78-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5c78-116">See also</span></span>

- [<span data-ttu-id="e5c78-117">Paralel Programlama için Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="e5c78-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
