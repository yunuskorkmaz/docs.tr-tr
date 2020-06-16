---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
description: Özel durumlar, verileri eşitleme, ön plan & arka plan iş parçacıkları, yerel depolama ve daha fazlası gibi konuları kapsayan diğer yönetilen iş parçacığı makalelerine yönelik bağlantılara bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769099"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="38cb1-103">Yönetilen iş parçacığı temelleri</span><span class="sxs-lookup"><span data-stu-id="38cb1-103">Managed threading basics</span></span>

<span data-ttu-id="38cb1-104">Bu bölümün ilk beş konusu, yönetilen iş parçacığı kullanmanın ne zaman kullanılacağını ve bazı temel özellikleri açıklamanıza yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="38cb1-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="38cb1-105">Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="38cb1-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="38cb1-106">Bu bölümdeki konuların geri kalanı, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38cb1-107">.NET Framework 4 ' te, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="38cb1-108">Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="38cb1-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38cb1-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="38cb1-109">In this section</span></span>

 [<span data-ttu-id="38cb1-110">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38cb1-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="38cb1-111">Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.</span><span class="sxs-lookup"><span data-stu-id="38cb1-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="38cb1-112">Yönetilen İş Parçacıklarında Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="38cb1-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="38cb1-113">Farklı .NET Framework sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırmasına neden oldukları durumları açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="38cb1-114">Çoklu İş Parçacığı Kullanımı için Veri Eşitleme</span><span class="sxs-lookup"><span data-stu-id="38cb1-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="38cb1-115">Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="38cb1-116">Ön Plan ve Arka Plan İş Parçacıkları</span><span class="sxs-lookup"><span data-stu-id="38cb1-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="38cb1-117">Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="38cb1-118">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38cb1-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="38cb1-119">Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.</span><span class="sxs-lookup"><span data-stu-id="38cb1-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="38cb1-120">İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları</span><span class="sxs-lookup"><span data-stu-id="38cb1-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="38cb1-121">İş parçacığı göreli depolama mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="38cb1-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="38cb1-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="38cb1-123">Yönetilen bir iş parçacığını temsil eden, yönetilmeyen koddan geldiği veya yönetilen bir uygulamada oluşturulup oluşturulmayacağı **Iş parçacığı** sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="38cb1-124">Kullanıcı arabirimi nesneleriyle birlikte çoklu iş parçacığı uygulama için güvenli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38cb1-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="38cb1-125">Related sections</span></span>

 [<span data-ttu-id="38cb1-126">Eşitleme temelleri 'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="38cb1-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="38cb1-127">Birden çok iş parçacığının etkinliklerini eşleştirmek için kullanılan yönetilen sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="38cb1-128">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="38cb1-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="38cb1-129">Çoklu iş parçacığı ve stratejilerle ilgili yaygın sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="38cb1-130">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="38cb1-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="38cb1-131">Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38cb1-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
