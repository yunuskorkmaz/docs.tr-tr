---
title: "Yönetilen İş Parçacığı Oluşturma Temelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 035834959aa5f9340727327b22cae93b3f21b056
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-threading-basics"></a><span data-ttu-id="8e960-102">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="8e960-102">Managed Threading Basics</span></span>
<span data-ttu-id="8e960-103">Bu bölümde, ilk beş konular yönetilen iş parçacığı oluşturma kullanın ve bazı temel özellikleri açıklamak için ne zaman belirlemenize yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e960-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="8e960-104">Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz: [iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="8e960-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="8e960-105">Bu bölümde kapak konularında kalan konular Windows işletim sistemiyle yönetilen iş parçacığı oluşturma etkileşimi dahil olmak üzere, Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="8e960-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e960-106">İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı ve PLINQ'da çok iş parçacıklı programlar görev ve veri paralellik için API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e960-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="8e960-107">Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e960-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e960-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8e960-108">In This Section</span></span>  
 [<span data-ttu-id="8e960-109">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e960-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="8e960-110">Avantajları ve dezavantajları birden çok iş parçacığı açıklar ve hangi iş parçacığı oluşturabilir veya iş parçacığı havuzu iş parçacıkları kullanın senaryoları özetler.</span><span class="sxs-lookup"><span data-stu-id="8e960-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="8e960-111">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8e960-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="8e960-112">.NET Framework'ün farklı sürümleri için iş parçacıklarında işlenmeyen özel durumlar davranışını durumlarda özellikle açıklar, bunlar sonlandırılmasıyla uygulamanın neden olarak.</span><span class="sxs-lookup"><span data-stu-id="8e960-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="8e960-113">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="8e960-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="8e960-114">Birden çok iş parçacığı ile kullanılacak sınıfları verileri eşitlemek için stratejilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e960-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="8e960-115">Yönetilen İş Parçacığı Durumları</span><span class="sxs-lookup"><span data-stu-id="8e960-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="8e960-116">Temel iş parçacığı durumları ve bir iş parçacığı çalışır durumda olup olmadığını algılamak nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e960-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="8e960-117">Ön Plan ve Arka Plan İş Parçacıkları</span><span class="sxs-lookup"><span data-stu-id="8e960-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="8e960-118">Ön ve arka plan iş parçacıkları arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e960-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="8e960-119">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e960-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="8e960-120">COM grupların ve yönetilen iş parçacığı etkileşimini açıklar ve yönetilen eşdeğerlerini API'leri iş parçacığı oluşturma Windows için listeler veya yönetilen ve yönetilmeyen iş parçacığı oluşturma arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e960-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="8e960-121">Thread.Suspend, Atık Toplama ve Güvenli Noktalar</span><span class="sxs-lookup"><span data-stu-id="8e960-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="8e960-122">İş parçacığı askıya alma ve atık toplama açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e960-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="8e960-123">İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları</span><span class="sxs-lookup"><span data-stu-id="8e960-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="8e960-124">İş parçacığı göreli depolama mekanizmaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e960-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="8e960-125">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="8e960-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="8e960-126">Ne zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler açıklayan bir iptal belirteci kullanarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e960-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8e960-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8e960-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="8e960-128">Başvuru belgelerine sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="8e960-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="8e960-129">Uygulamak için güvenli bir yol sağlar kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="8e960-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e960-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e960-130">Related Sections</span></span>  
 [<span data-ttu-id="8e960-131">Eşitleme Temellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e960-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="8e960-132">Birden çok iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen sınıflar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e960-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="8e960-133">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="8e960-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="8e960-134">Yaygın sorunları açıklar çoklu iş parçacığı kullanımı ve sorunlarını stratejileri.</span><span class="sxs-lookup"><span data-stu-id="8e960-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="8e960-135">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="8e960-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="8e960-136">Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştırma görev paralel kitaplığı ve PLINQ'da, açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e960-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
