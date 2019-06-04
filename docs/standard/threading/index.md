---
title: Yönetilen İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f51920bceef6e83af4f6ef029eb49ae495a58b9b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490851"
---
# <a name="managed-threading"></a><span data-ttu-id="01a70-102">Yönetilen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a70-102">Managed Threading</span></span>
<span data-ttu-id="01a70-103">Bir işlemci veya birçok bilgisayarla geliştirmekte olduğunuz olup olmadığını uygulama şu anda diğer iş yapıyor olsanız bile, uygulamanızın en hızlı yanıt veren kullanıcı etkileşimi sağlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="01a70-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="01a70-104">Birden çok iş parçacığı yürütme kullanmaktır, uygulamanızın kullanıcı yanıt veren tutun ve aynı anda en güçlü yollarından biri işlemci arasında veya kullanıcı olayları sırasında bile kullanın.</span><span class="sxs-lookup"><span data-stu-id="01a70-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="01a70-105">Bu bölümde, iş parçacığı temel kavramları açıklar, ancak yönetilen iş parçacığı kavramları ve yönetilen iş parçacığı kullanarak odaklanır.</span><span class="sxs-lookup"><span data-stu-id="01a70-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01a70-106">.NET Framework 4 ile başlayarak, çok iş parçacıklı programlama büyük ölçüde ile basitleştirilmiştir <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), yeni eşzamanlı koleksiyon sınıflarını içinde <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramını temel alarak yeni bir programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="01a70-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="01a70-107">Daha fazla bilgi için [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="01a70-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01a70-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="01a70-108">In This Section</span></span>  
 [<span data-ttu-id="01a70-109">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="01a70-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="01a70-110">Yönetilen iş parçacığı genel bir bakış sağlar ve ne zaman birden çok iş parçacığı kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="01a70-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="01a70-111">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="01a70-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="01a70-112">Oluşturma, Başlat, duraklatma, sürdürme ve iş parçacıklarını durdurma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01a70-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="01a70-113">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="01a70-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="01a70-114">Düzeyleri açıklar, eşitleme sorunları nasıl Kilitlenmeler ve yarış durumları ve diğer iş parçacığı önlemek.</span><span class="sxs-lookup"><span data-stu-id="01a70-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="01a70-115">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="01a70-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="01a70-116">İş parçacıkları etkinliklerini ve nesnelerin farklı iş parçacıklarında erişilen verileri eşitlemek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıkları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a70-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="01a70-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="01a70-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="01a70-118">Yönetilen iş parçacıklarını eşitleme ve kullanma için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="01a70-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="01a70-119">Birden çok iş parçacığı ile kullanmak için güvenli koleksiyon sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="01a70-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="01a70-120">Oluşturma ve eş zamanlı işleme görevleri zamanlamak için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="01a70-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="01a70-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="01a70-121">Related Sections</span></span>  
 [<span data-ttu-id="01a70-122">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="01a70-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="01a70-123">Uygulama etki alanları ve bunların kullanılması ortak dil altyapısı tarafından genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a70-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="01a70-124">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="01a70-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="01a70-125">Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.</span><span class="sxs-lookup"><span data-stu-id="01a70-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="01a70-126">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="01a70-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="01a70-127">. NET'te zaman uyumsuz programlama için önerilen düzene genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a70-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="01a70-128">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="01a70-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="01a70-129">Temsilciler'ın yerleşik özelliklerini kullanarak havuzu iş parçacıkları iş parçacığı üzerinde yöntemleri çağırmak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="01a70-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="01a70-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="01a70-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="01a70-131">Paralel Programlama uygulamalarda birden çok iş parçacığı kullanımını basitleştiren kitaplıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="01a70-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="01a70-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="01a70-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="01a70-133">Birden çok işlemci yararlanmak için paralel sorgular çalıştırmak için bir sistem açıklar.</span><span class="sxs-lookup"><span data-stu-id="01a70-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
