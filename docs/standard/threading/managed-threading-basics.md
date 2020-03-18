---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139235"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="99696-102">Yönetilen iş parçacığı temelleri</span><span class="sxs-lookup"><span data-stu-id="99696-102">Managed threading basics</span></span>

<span data-ttu-id="99696-103">Bu bölümün ilk beş konusu, yönetilen iş parçacığının ne zaman kullanılacağını belirlemenize ve bazı temel özellikleri açıklamanıza yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="99696-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="99696-104">Ek özellikler sağlayan sınıflar hakkında bilgi için [bkz.](../../../docs/standard/threading/threading-objects-and-features.md) [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)</span><span class="sxs-lookup"><span data-stu-id="99696-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="99696-105">Bu bölümdeki diğer konular, yönetilen iş parçacığının Windows işletim sistemiyle etkileşimi de dahil olmak üzere gelişmiş konuları kapsamaktadır.</span><span class="sxs-lookup"><span data-stu-id="99696-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99696-106">.NET Framework 4'te, Görev Paralel Kitaplığı ve PLINQ çok iş parçacığı lı programlarda görev ve veri paralelliği için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="99696-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="99696-107">Daha fazla bilgi için [Bkz. Paralel Programlama.](../../../docs/standard/parallel-programming/index.md)</span><span class="sxs-lookup"><span data-stu-id="99696-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99696-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="99696-108">In this section</span></span>

 [<span data-ttu-id="99696-109">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99696-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="99696-110">Birden çok iş parçacığının avantajlarını ve dezavantajlarını tartışır ve iş parçacığı oluşturabileceğiniz veya iş parçacığı havuzu iş parçacığı iş parçacığı kullanabileceğiniz senaryoları özetler.</span><span class="sxs-lookup"><span data-stu-id="99696-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="99696-111">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="99696-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="99696-112">.NET Framework'ün farklı sürümleri için işlenmemiş özel durumların davranışını, özellikle de uygulamanın sonlandırılmasıyla sonuçlanan durumları açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="99696-113">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="99696-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="99696-114">Birden çok iş parçacığı ile kullanılacak sınıflarda verileri eşitleme stratejilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="99696-115">Ön Plan ve Arka Plan İş Parçacıkları</span><span class="sxs-lookup"><span data-stu-id="99696-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="99696-116">Ön plan ve arka plan iş parçacıkları arasındaki farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="99696-117">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99696-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="99696-118">Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi tartışır, Windows iş parçacığı API'leri için yönetilen eşdeğerleri listeler ve COM daireleri ve yönetilen iş parçacıklarının etkileşimini tartışır.</span><span class="sxs-lookup"><span data-stu-id="99696-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="99696-119">İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları</span><span class="sxs-lookup"><span data-stu-id="99696-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="99696-120">İş parçacığı göreli depolama mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99696-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="99696-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="99696-122">Yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan olsun, yönetilen bir iş parçacığı temsil eden **İş Parçacığı** sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="99696-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="99696-123">Kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı uygulamak için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="99696-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99696-124">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="99696-124">Related sections</span></span>

 [<span data-ttu-id="99696-125">Senkronizasyon İlkellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99696-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="99696-126">Birden çok iş parçacığının etkinliklerini eşitlemek için kullanılan yönetilen sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="99696-127">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="99696-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="99696-128">Çok iş parçacığı ile ilgili yaygın sorunları ve sorunları önlemek için stratejiler açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="99696-129">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="99696-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="99696-130">Asynchronous ve çok iş parçacığı .NET Framework uygulamaları oluşturma işini büyük ölçüde basitleştiren Görev Paralel Kitaplığı ve PLINQ'u açıklar.</span><span class="sxs-lookup"><span data-stu-id="99696-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
