---
title: "Okuyucu-Yazıcı Kilitleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d005442ee74b46a0ecb1eaafe214e7190330cfe7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="reader-writer-locks"></a><span data-ttu-id="82994-102">Okuyucu-Yazıcı Kilitleri</span><span class="sxs-lookup"><span data-stu-id="82994-102">Reader-Writer Locks</span></span>
<span data-ttu-id="82994-103"><xref:System.Threading.ReaderWriterLockSlim> Sınıfı bir kaynak eşzamanlı olarak okumak birden çok iş parçacığı sağlar, ancak özel bir kilit için kaynağa yazma için beklenecek bir iş parçacığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82994-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="82994-104">Kullanabileceğinize bir <xref:System.Threading.ReaderWriterLockSlim> bir paylaşılan kaynağa erişim iş parçacıkları arasında işbirlikçi eşitleme sağlamak için uygulamanızda.</span><span class="sxs-lookup"><span data-stu-id="82994-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="82994-105">Kilitleri alınır <xref:System.Threading.ReaderWriterLockSlim> kendisi.</span><span class="sxs-lookup"><span data-stu-id="82994-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="82994-106">Hiçbir iş parçacığı eşitleme mekanizması ile iş parçacığı tarafından sağlanan kilitleme atlama sağlamalısınız gibi <xref:System.Threading.ReaderWriterLockSlim>.</span><span class="sxs-lookup"><span data-stu-id="82994-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="82994-107">Bunu sağlamak için bir paylaşılan kaynağa yalıtan bir sınıf tasarlamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="82994-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="82994-108">Bu sınıf özel paylaşılan kaynağa erişme ve özel kullanma üyeleri sağlayacak <xref:System.Threading.ReaderWriterLockSlim> eşitleme için.</span><span class="sxs-lookup"><span data-stu-id="82994-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="82994-109">Örneğin, kod örneğine bakın <xref:System.Threading.ReaderWriterLockSlim> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="82994-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="82994-110"><xref:System.Threading.ReaderWriterLockSlim>ayrı ayrı nesneleri eşitlemek için kullanılacak verimli olur.</span><span class="sxs-lookup"><span data-stu-id="82994-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="82994-111">Uygulamanızın Okuma süresini en aza indirmek ve yazma işlemleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="82994-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="82994-112">Yazma kilidi özel olduğundan uzun yazma işlemleri işleme doğrudan etkiler.</span><span class="sxs-lookup"><span data-stu-id="82994-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="82994-113">Uzun işlemleri blok bekleme yazıcılarının okuma ve yazma erişimi için en az bir iş parçacığı bekliyorsa okuma erişimi isteği iş parçacığı de engellenir.</span><span class="sxs-lookup"><span data-stu-id="82994-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82994-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İki Okuyucu-Yazıcı kilitleri sahip <xref:System.Threading.ReaderWriterLockSlim> ve <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="82994-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="82994-115"><xref:System.Threading.ReaderWriterLockSlim>tüm yeni geliştirme projeleri için önerilir.</span><span class="sxs-lookup"><span data-stu-id="82994-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="82994-116"><xref:System.Threading.ReaderWriterLockSlim>benzer <xref:System.Threading.ReaderWriterLock>, ancak kurallar ve yükseltme ve kilitleme durumu eski sürüme düşürmeyi özyineleme için basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82994-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="82994-117"><xref:System.Threading.ReaderWriterLockSlim>olası kilitlenme birçok örneklerini önler.</span><span class="sxs-lookup"><span data-stu-id="82994-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="82994-118">Ayrıca, performansını <xref:System.Threading.ReaderWriterLockSlim> daha önemli ölçüde iyidir <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="82994-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82994-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82994-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="82994-120">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="82994-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="82994-121">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="82994-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
