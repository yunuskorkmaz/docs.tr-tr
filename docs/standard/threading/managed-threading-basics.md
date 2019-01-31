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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e053a04ba0587a4eca166fa710bc465094feca80
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479574"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="9319e-102">Yönetilen iş parçacığı oluşturma temelleri</span><span class="sxs-lookup"><span data-stu-id="9319e-102">Managed threading basics</span></span>

<span data-ttu-id="9319e-103">Bu bölümün ilk beş konular, yönetilen iş parçacığı kullanılacağını ve bazı temel özellikleri açıklamak için ne zaman belirlemenize yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9319e-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="9319e-104">Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz: [iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="9319e-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="9319e-105">Bu bölümde kapak konularındaki geri kalanı Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi gibi konuları, Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="9319e-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9319e-106">İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı ve PLINQ'da çok iş parçacıklı programlarda görev ve veri paralelliği için API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9319e-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="9319e-107">Daha fazla bilgi için [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="9319e-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9319e-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="9319e-108">In this section</span></span>

 [<span data-ttu-id="9319e-109">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9319e-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="9319e-110">Avantajları ve dezavantajları birden çok iş parçacığı ele alır ve hangi iş parçacıkları oluşturma veya iş parçacığı havuzu iş parçacıkları kullanma senaryoları özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9319e-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="9319e-111">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9319e-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="9319e-112">İşlenmeyen özel durumlar .NET Framework'ün farklı sürümleri için iş parçacıklarında davranışını özellikle durumlar açıklanır, bunlar uygulama sonlandırmada neden olarak.</span><span class="sxs-lookup"><span data-stu-id="9319e-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="9319e-113">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="9319e-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="9319e-114">Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemek için stratejilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9319e-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="9319e-115">Ön Plan ve Arka Plan İş Parçacıkları</span><span class="sxs-lookup"><span data-stu-id="9319e-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="9319e-116">Ön ve arka plan iş parçacıkları arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9319e-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="9319e-117">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9319e-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="9319e-118">Yönetilen ve yönetilmeyen iş parçacığı oluşturma arasındaki ilişkiyi açıklar, Windows API iş parçacığı için yönetilen eşdeğerlerini listeler ve COM apartmanlar ve yönetilen iş parçacıklarını etkileşimi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9319e-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="9319e-119">Thread.Suspend, Atık Toplama ve Güvenli Noktalar</span><span class="sxs-lookup"><span data-stu-id="9319e-119">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="9319e-120">İş parçacığını askıya alma ve atık toplama açıklar.</span><span class="sxs-lookup"><span data-stu-id="9319e-120">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="9319e-121">İş parçacığı yerel deposu: İş parçacığı göreli statik alanları ve veri yuvaları</span><span class="sxs-lookup"><span data-stu-id="9319e-121">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="9319e-122">İş parçacığı göreli depolama mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9319e-122">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="9319e-123">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="9319e-123">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="9319e-124">Ne zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemlerini açıklayan bir iptal belirteci kullanarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9319e-124">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9319e-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9319e-125">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="9319e-126">İçin başvuru belgeleri sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan yönetilen iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="9319e-126">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="9319e-127">Uygulamak için güvenli bir yol sağlayan kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="9319e-127">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9319e-128">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="9319e-128">Related sections</span></span>

 [<span data-ttu-id="9319e-129">Eşitleme Temellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9319e-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="9319e-130">Birden çok iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen sınıflar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9319e-130">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="9319e-131">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="9319e-131">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="9319e-132">Ortak sorunları açıklar çoklu iş parçacığı kullanımı ve stratejileri sorunlarını önleme.</span><span class="sxs-lookup"><span data-stu-id="9319e-132">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="9319e-133">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="9319e-133">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="9319e-134">Görev paralel kitaplığı ve PLINQ'da, zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde basitleştiren açıklar.</span><span class="sxs-lookup"><span data-stu-id="9319e-134">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
