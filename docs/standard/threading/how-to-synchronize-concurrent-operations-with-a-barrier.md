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
ms.openlocfilehash: 4a2dc5e650a479e782a6739a82e247c25e196fda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583159"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="0d194-102">Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme</span><span class="sxs-lookup"><span data-stu-id="0d194-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="0d194-103">Aşağıdaki örnek, eş zamanlı görevleri ile eşitlemek gösterilmiştir bir <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="0d194-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d194-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d194-104">Example</span></span>  
 <span data-ttu-id="0d194-105">Aşağıdaki programı amacı kaç yineleme (veya aşamaları) sayısı için her bulma için iki iş parçacığı için çözümü kendi yarısı aynı aşamaya sözcükleri sırasını yeniden ayarlaması randomizing bir algoritma kullanarak gereken budur.</span><span class="sxs-lookup"><span data-stu-id="0d194-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="0d194-106">Her iş parçacığının kendi sözcükler karışık sonra engel sonrası aşaması işlemi tam bir cümle doğru word sırada işlenip işlenmediğini görmek için iki sonucu karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0d194-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="0d194-107">A <xref:System.Threading.Barrier> tüm görevler engel ulaşana kadar devam etmeden bir paralel işlemin tek tek görevlere engelleyen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="0d194-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="0d194-108">Paralel işlem aşamada gerçekleşir ve her aşamada görevler arasında eşitleme gerektirdiğinde yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0d194-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="0d194-109">Bu örnekte, işlem için iki aşama vardır.</span><span class="sxs-lookup"><span data-stu-id="0d194-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="0d194-110">İlk aşamada, her görev kendi bölümüne arabellek verilerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="0d194-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="0d194-111">Her görev kendi bölümüne doldurma tamamlandığında, görev devam etmeye hazır engel ve bekler işaret eder.</span><span class="sxs-lookup"><span data-stu-id="0d194-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="0d194-112">Tüm Görevler engel işaret engeli ve ikinci aşaması başlar.</span><span class="sxs-lookup"><span data-stu-id="0d194-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="0d194-113">İkinci aşama her görev, bu noktaya kadar üretilen tüm verilere erişimi olmasını gerektirdiğinden engel gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0d194-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="0d194-114">Engel ilk görevlerinin tamamlanması için henüz diğer görevler tarafından doldurulmuştur olmayan arabellekler okunacak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d194-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="0d194-115">Bu şekilde aşamada herhangi bir sayıda eşitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d194-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d194-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d194-116">See Also</span></span>  
 [<span data-ttu-id="0d194-117">Paralel Programlama için Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="0d194-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
