---
title: "Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="d325f-102">Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma</span><span class="sxs-lookup"><span data-stu-id="d325f-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="d325f-103">Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="d325f-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d325f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d325f-104">Example</span></span>  
 <span data-ttu-id="d325f-105">Bu örnekte, en az miktarda iyi bir aday kolaylaştırır için iş kritik bölüm gerçekleştiren bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="d325f-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="d325f-106">İş artırılması küçük bir miktar performansını artırır <xref:System.Threading.SpinLock> standart kilit karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="d325f-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="d325f-107">Ancak bir SpinLock standart kilit daha pahalı hale noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="d325f-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="d325f-108">Hangi tür kilit programınızdaki daha iyi performans sağlar görmek için profil oluşturma araçları işlevindeki profil eşzamanlılık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d325f-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="d325f-109">Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="d325f-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="d325f-110"><xref:System.Threading.SpinLock>Paylaşılan bir kaynak üzerinde bir kilit için tutulması gonna yararlı olabilir çok uzun.</span><span class="sxs-lookup"><span data-stu-id="d325f-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="d325f-111">Böyle durumlarda, çok çekirdekli bilgisayarlarda bu kilidi serbest kadar birkaç döngüsü boyunca dönmeye engellenmiş iş parçacığı için etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="d325f-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="d325f-112">Dönen tarafından iş parçacığı, hangi CPU yoğunluklu bir işlemdir engellenmiş duruma değil.</span><span class="sxs-lookup"><span data-stu-id="d325f-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="d325f-113"><xref:System.Threading.SpinLock>mantıksal işlemci veya Hyper-Threading sistemleriyle öncelik ters çevirmeyi engellenmiştir belirli koşullar altında dönen durdurur.</span><span class="sxs-lookup"><span data-stu-id="d325f-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="d325f-114">Bu örnekte <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> kullanıcı eşitleme için çok iş parçacıklı erişmesi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d325f-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="d325f-115">.NET Framework sürüm 4 hedef uygulamalarda, başka bir seçenek kullanmaktır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, kullanıcı kilitleri gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d325f-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="d325f-116">Kullanımına dikkat edin `false` (`False` Visual Basic'te) çağrısında <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="d325f-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="d325f-117">Bu, en iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="d325f-117">This provides the best performance.</span></span> <span data-ttu-id="d325f-118">Belirtin `true` (`True`) bellek sınırı kullanmak için IA64 mimarileri üzerinde hangi boşaltır kilidi çıkmak başka bir iş parçacığı için kullanılabilir olduğundan emin olmak için yazma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="d325f-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d325f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d325f-119">See Also</span></span>  
 [<span data-ttu-id="d325f-120">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="d325f-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
