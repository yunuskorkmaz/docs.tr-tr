---
title: 'Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma'
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
ms.openlocfilehash: 216480e893f6dbebbb204cbf2bfebae8dc139ec4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190708"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="031ef-102">Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma</span><span class="sxs-lookup"><span data-stu-id="031ef-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="031ef-103">Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="031ef-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="031ef-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="031ef-104">Example</span></span>  
 <span data-ttu-id="031ef-105">Bu örnekte, kritik bölüm için iyi bir aday hale getiren iş en az miktarda gerçekleştiren bir <xref:System.Threading.SpinLock>.</span><span class="sxs-lookup"><span data-stu-id="031ef-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="031ef-106">Artan iş küçük bir miktar performansını artırır <xref:System.Threading.SpinLock> standart kilit karşılaştırılan.</span><span class="sxs-lookup"><span data-stu-id="031ef-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="031ef-107">Bununla birlikte, başlangıçtan bir SpinLock standart bir kilit daha pahalı olur bir noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="031ef-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="031ef-108">Kilit türü programınızdaki daha iyi performans sağlar görmek için profil oluşturma profil oluşturma araçlarındaki işlevselliği eşzamanlılık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="031ef-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="031ef-109">Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="031ef-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="031ef-110"><xref:System.Threading.SpinLock> Paylaşılan kaynakta kilit yönelik zaman yararlı olabileceği çok uzun.</span><span class="sxs-lookup"><span data-stu-id="031ef-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="031ef-111">Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit yayımlanana kadar birkaç döngülerini dönmeye engellenmiş iş parçacığı için verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="031ef-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="031ef-112">Dönen tarafından iş parçacığı, hangi CPU yoğunluklu bir işlemdir engellenmediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="031ef-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="031ef-113"><xref:System.Threading.SpinLock> mantıksal işlemci veya Hyper-Threading sistemleriyle öncelik ters çevirmeyi engellenmiştir belirli koşullar altında dönen durdurur.</span><span class="sxs-lookup"><span data-stu-id="031ef-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="031ef-114">Bu örnekte <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfını kullanıcı eşitleme için çok iş parçacıklı erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="031ef-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="031ef-115">.NET Framework sürüm 4'ü hedefleyen uygulamalar, başka bir seçenek kullanmaktır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, kullanıcı kilitleri gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="031ef-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="031ef-116">Kullanımına dikkat edin `false` (`False` Visual Basic'te) çağrısında <xref:System.Threading.SpinLock.Exit%2A>.</span><span class="sxs-lookup"><span data-stu-id="031ef-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="031ef-117">Bu, en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="031ef-117">This provides the best performance.</span></span> <span data-ttu-id="031ef-118">Belirtin `true` (`True`) IA64 mimariler bellek sınırı kullanmak için hangi aktarır kilit çıkmak diğer iş parçacıkları için kullanılabilir olmasını sağlamak için yazma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="031ef-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031ef-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="031ef-119">See also</span></span>

- [<span data-ttu-id="031ef-120">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="031ef-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
