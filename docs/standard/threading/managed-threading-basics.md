---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
description: Özel durumlar, verileri eşitleme, ön plan & arka plan iş parçacıkları, yerel depolama ve daha fazlası gibi konuları kapsayan diğer yönetilen iş parçacığı makalelerine yönelik bağlantılara bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- multiple threads
- threading [.NET], multiple threads
- threading [.NET], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 16785b1c21c5810e55429f6756dcf591c90d8499
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819675"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="22081-103">Yönetilen iş parçacığı temelleri</span><span class="sxs-lookup"><span data-stu-id="22081-103">Managed threading basics</span></span>

<span data-ttu-id="22081-104">Bu bölümün ilk beş makalesi, yönetilen iş parçacığı oluşturmayı ve bazı temel özellikleri açıklamak için ne zaman kullanacağınızı belirlemenize yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="22081-104">The first five articles of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="22081-105">Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="22081-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="22081-106">Bu bölümdeki diğer makaleler, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.</span><span class="sxs-lookup"><span data-stu-id="22081-106">The remaining articles in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22081-107">.NET Framework 4 ' den başlayarak, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="22081-107">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="22081-108">Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="22081-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22081-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="22081-109">In this section</span></span>

 [<span data-ttu-id="22081-110">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="22081-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="22081-111">Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.</span><span class="sxs-lookup"><span data-stu-id="22081-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="22081-112">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="22081-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="22081-113">.NET 'in farklı sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırılması ile sonuçlandığı durumlarda açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-113">Describes the behavior of unhandled exceptions in threads for different versions of .NET, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="22081-114">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="22081-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="22081-115">Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="22081-116">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="22081-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="22081-117">Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="22081-118">Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="22081-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="22081-119">Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.</span><span class="sxs-lookup"><span data-stu-id="22081-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="22081-120">İş Parçacığında Yerel Depolama: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları</span><span class="sxs-lookup"><span data-stu-id="22081-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="22081-121">İş parçacığı göreli depolama mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="22081-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="22081-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="22081-123">Yönetilen bir iş parçacığını temsil eden, yönetilmeyen koddan geldiği veya yönetilen bir uygulamada oluşturulup oluşturulmayacağı **Iş parçacığı** sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="22081-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="22081-124">Kullanıcı arabirimi nesneleriyle birlikte çoklu iş parçacığı uygulama için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="22081-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="22081-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="22081-125">Related sections</span></span>

 [<span data-ttu-id="22081-126">Eşitleme temelleri 'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="22081-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="22081-127">Birden çok iş parçacığının etkinliklerini eşleştirmek için kullanılan yönetilen sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="22081-128">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="22081-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="22081-129">Çoklu iş parçacığı ve stratejilerle ilgili yaygın sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="22081-130">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="22081-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="22081-131">Zaman uyumsuz ve çok iş parçacıklı .NET uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.</span><span class="sxs-lookup"><span data-stu-id="22081-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET applications.</span></span>
