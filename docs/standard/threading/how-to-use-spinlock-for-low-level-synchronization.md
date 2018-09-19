---
title: 'Nasıl yapılır: düşük düzeyli eşitleme için SpinLock kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff604b94ecef1ffec5fe9845df7c5ba35f5857d7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000274"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="14fb5-102">Nasıl yapılır: düşük düzeyli eşitleme için SpinLock kullanma</span><span class="sxs-lookup"><span data-stu-id="14fb5-102">How to: use SpinLock for low-level synchronization</span></span>

<span data-ttu-id="14fb5-103">Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="14fb5-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="14fb5-104">Bu örnekte, kritik bölüm için iyi bir aday hale getiren iş en az miktarda gerçekleştiren bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="14fb5-104">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="14fb5-105">Artan iş küçük bir miktar performansını artırır <xref:System.Threading.SpinLock> standart kilit karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="14fb5-105">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="14fb5-106">Bununla birlikte, başlangıçtan bir SpinLock standart bir kilit daha pahalı olur bir noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="14fb5-106">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="14fb5-107">Kilit türü programınızdaki daha iyi performans sağlar görmek için profil oluşturma profil oluşturma araçlarındaki işlevselliği eşzamanlılık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14fb5-107">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="14fb5-108">Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="14fb5-108">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="14fb5-109"><xref:System.Threading.SpinLock> Paylaşılan kaynakta kilit yönelik zaman yararlı olabileceği çok uzun.</span><span class="sxs-lookup"><span data-stu-id="14fb5-109"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="14fb5-110">Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit yayımlanana kadar birkaç döngülerini dönmeye engellenmiş iş parçacığı için verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="14fb5-110">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="14fb5-111">Dönen tarafından iş parçacığı, hangi CPU yoğunluklu bir işlemdir engellenmediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="14fb5-111">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="14fb5-112"><xref:System.Threading.SpinLock> mantıksal işlemci veya Hyper-Threading sistemleriyle öncelik ters çevirmeyi engellenmiştir belirli koşullar altında dönen durdurur.</span><span class="sxs-lookup"><span data-stu-id="14fb5-112"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="14fb5-113">Bu örnekte <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfını kullanıcı eşitleme için çok iş parçacıklı erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="14fb5-113">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="14fb5-114">.NET Framework sürüm 4'ü hedefleyen uygulamalar, başka bir seçenek kullanmaktır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, kullanıcı kilitleri gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="14fb5-114">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="14fb5-115">Kullanımına dikkat edin `false` (`False` Visual Basic'te) çağrısında <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14fb5-115">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="14fb5-116">Bu, en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14fb5-116">This provides the best performance.</span></span> <span data-ttu-id="14fb5-117">Belirtin `true` (`True` Visual Basic'te) IA64 mimariler bellek sınırı kullanmak için hangi aktarır kilit çıkmak diğer iş parçacıkları için kullanılabilir olmasını sağlamak için yazma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="14fb5-117">Specify `true` (`True` in Visual Basic) on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fb5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14fb5-118">See also</span></span>

- [<span data-ttu-id="14fb5-119">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="14fb5-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="14fb5-120">lock deyimi (C#)</span><span class="sxs-lookup"><span data-stu-id="14fb5-120">lock statement (C#)</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
- [<span data-ttu-id="14fb5-121">SyncLock deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14fb5-121">SyncLock statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/synclock-statement.md)
