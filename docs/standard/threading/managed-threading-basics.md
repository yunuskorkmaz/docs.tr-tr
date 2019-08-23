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
ms.openlocfilehash: f55057e40a251be49898b9b1b7862bd243b2a70c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913175"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="3d92d-102">Yönetilen iş parçacığı temelleri</span><span class="sxs-lookup"><span data-stu-id="3d92d-102">Managed threading basics</span></span>

<span data-ttu-id="3d92d-103">Bu bölümün ilk beş konusu, yönetilen iş parçacığı kullanmanın ne zaman kullanılacağını ve bazı temel özellikleri açıklamanıza yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3d92d-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="3d92d-104">Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="3d92d-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="3d92d-105">Bu bölümdeki konuların geri kalanı, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d92d-106">.NET Framework 4 ' te, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="3d92d-107">Daha fazla bilgi için bkz. [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d92d-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d92d-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="3d92d-108">In this section</span></span>

 [<span data-ttu-id="3d92d-109">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d92d-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="3d92d-110">Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.</span><span class="sxs-lookup"><span data-stu-id="3d92d-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="3d92d-111">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="3d92d-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="3d92d-112">Farklı .NET Framework sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırmasına neden oldukları durumları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="3d92d-113">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="3d92d-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="3d92d-114">Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="3d92d-115">Ön Plan ve Arka Plan İş Parçacıkları</span><span class="sxs-lookup"><span data-stu-id="3d92d-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="3d92d-116">Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="3d92d-117">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d92d-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="3d92d-118">Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.</span><span class="sxs-lookup"><span data-stu-id="3d92d-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="3d92d-119">İş parçacığı yerel depolaması: İş parçacığı göreli statik alanları ve veri yuvaları</span><span class="sxs-lookup"><span data-stu-id="3d92d-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="3d92d-120">İş parçacığı göreli depolama mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3d92d-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3d92d-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="3d92d-122">Yönetilen bir iş parçacığını temsil eden, yönetilmeyen koddan geldiği veya yönetilen bir uygulamada oluşturulup oluşturulmayacağı **Iş parçacığı** sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="3d92d-123">Kullanıcı arabirimi nesneleriyle birlikte çoklu iş parçacığı uygulama için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d92d-124">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="3d92d-124">Related sections</span></span>

 [<span data-ttu-id="3d92d-125">Eşitleme Temellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d92d-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="3d92d-126">Birden çok iş parçacığının etkinliklerini eşleştirmek için kullanılan yönetilen sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="3d92d-127">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3d92d-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="3d92d-128">Çoklu iş parçacığı ve stratejilerle ilgili yaygın sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="3d92d-129">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="3d92d-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="3d92d-130">Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d92d-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
