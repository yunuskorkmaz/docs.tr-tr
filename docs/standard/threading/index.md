---
title: "Yönetilen İş Parçacığı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61cd2317b5690573532af2a25c0b84b1fe136fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading"></a><span data-ttu-id="47a99-102">Yönetilen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47a99-102">Managed Threading</span></span>
<span data-ttu-id="47a99-103">Bir işlemci veya birkaç sahip bilgisayarlar için geliştirdiğiniz olup olmadığını uygulama şu anda diğer iş yaptığını olsa bile kullanıcının en esnek etkileşim sağlamak için uygulamanızın istiyor.</span><span class="sxs-lookup"><span data-stu-id="47a99-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="47a99-104">Birden çok iş parçacığı yürütme kullanmaktır, uygulamanızın yanıt vereceğini kullanıcıya tutun ve aynı anda yapmak için en güçlü şekilde arasındaki veya kullanıcı olayları sırasında bile işlemcinin kullanın.</span><span class="sxs-lookup"><span data-stu-id="47a99-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="47a99-105">Bu bölüm iş parçacığı oluşturma temel kavramları tanıtır olsa da, yönetilen kavramları iş parçacığı oluşturma ve yönetilen iş parçacığı kullanarak odaklanır.</span><span class="sxs-lookup"><span data-stu-id="47a99-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47a99-106">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], birden çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramı dayalı yeni bir programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="47a99-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="47a99-107">Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="47a99-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47a99-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="47a99-108">In This Section</span></span>  
 [<span data-ttu-id="47a99-109">Yönetilen iş parçacığı oluşturma temelleri</span><span class="sxs-lookup"><span data-stu-id="47a99-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="47a99-110">Yönetilen iş parçacığı oluşturma genel bir bakış sağlar ve ne zaman birden çok iş parçacığı kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="47a99-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="47a99-111">İş parçacığı kullanma ve iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="47a99-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="47a99-112">Oluştur, Başlat, duraklatma, sürdürme ve iş parçacıklarını durdurma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47a99-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="47a99-113">Yönetilen iş parçacığı oluşturma en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="47a99-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="47a99-114">Eşitleme, Kilitlenmeler ve yarış durumları, tek işlemcili önlemenin ve çok işlemcili bilgisayarlar ve diğer iş parçacığı oluşturma sorunları düzeylerini açıklanır.</span><span class="sxs-lookup"><span data-stu-id="47a99-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, single-processor and multiprocessor computers, and other threading issues.</span></span>  
  
 [<span data-ttu-id="47a99-115">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="47a99-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="47a99-116">İş parçacığı etkinliklerini ve farklı iş parçacıklarında erişilen nesneler verileri eşitlemek için kullanabileceğiniz yönetilen sınıflar açıklar ve iş parçacığı havuzu iş parçacıkları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="47a99-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="47a99-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="47a99-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="47a99-118">Kullanarak ve yönetilen iş parçacıklarını eşitleme için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="47a99-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="47a99-119">Birden çok iş parçacığı ile kullanmak için güvenli koleksiyon sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="47a99-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="47a99-120">Oluşturma ve eş zamanlı işleme görevlerini zamanlama için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="47a99-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47a99-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="47a99-121">Related Sections</span></span>  
 [<span data-ttu-id="47a99-122">Uygulama etki alanları</span><span class="sxs-lookup"><span data-stu-id="47a99-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="47a99-123">Uygulama etki alanları ve bunların kullanılması ortak dil altyapısı tarafından genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="47a99-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="47a99-124">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="47a99-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="47a99-125">Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.</span><span class="sxs-lookup"><span data-stu-id="47a99-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="47a99-126">Olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="47a99-126">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="47a99-127">Zaman uyumsuz programlama genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="47a99-127">Provides an overview of asynchronous programming.</span></span>  
  
 [<span data-ttu-id="47a99-128">Zaman uyumlu yöntemleri zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="47a99-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="47a99-129">İş parçacığı üzerinde temsilciler yerleşik özelliklerini kullanarak havuzu iş parçacıkları yöntemlerini çağırmaya açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47a99-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="47a99-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="47a99-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="47a99-131">Paralel uygulamalar içindeki birden çok iş parçacığı kullanımını kolaylaştırmak kitaplıkları programlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="47a99-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="47a99-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="47a99-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="47a99-133">Birden çok işlemci yararlanmak için paralel sorgular çalıştırmak için bir sistem açıklar.</span><span class="sxs-lookup"><span data-stu-id="47a99-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
