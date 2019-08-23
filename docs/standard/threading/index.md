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
ms.openlocfilehash: 763646bfb358b8e5faf13a14f2facb98f855b5c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913277"
---
# <a name="managed-threading"></a><span data-ttu-id="13623-102">Yönetilen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="13623-102">Managed Threading</span></span>
<span data-ttu-id="13623-103">Tek bir işlemciye veya birkaç kullanıcıya sahip bilgisayarlar için geliştirme olsanız da, uygulama şu anda başka bir iş yapıyor olsa bile, uygulamanızın kullanıcıyla en iyi yanıt verme etkileşimini sağlamasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="13623-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="13623-104">Birden çok iş parçacığının kullanılması, uygulamanızı kullanıcıya yanıt vermenin en güçlü yöntemlerinden biridir ve aynı zamanda Kullanıcı olayları sırasında veya hatta içinde işlemciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="13623-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="13623-105">Bu bölümde iş parçacığı temel kavramları tanıtılırken, yönetilen iş parçacığı kavramlarıyla ve yönetilen iş parçacığı kullanımıyla odaklanır.</span><span class="sxs-lookup"><span data-stu-id="13623-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13623-106">.NET Framework 4 ' te başlayarak çok iş parçacıklı programlama <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> , ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları, [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) <xref:System.Collections.Concurrent?displayProperty=nameWithType> , ad alanındaki yeni eşzamanlı koleksiyon sınıfları ve yeni bir programlama ile büyük ölçüde basitleştirilmiştir iş parçacıkları yerine görev kavramını temel alan model.</span><span class="sxs-lookup"><span data-stu-id="13623-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="13623-107">Daha fazla bilgi için bkz. [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="13623-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13623-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="13623-108">In This Section</span></span>  
 [<span data-ttu-id="13623-109">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="13623-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="13623-110">Yönetilen iş parçacığına genel bir bakış sağlar ve birden çok iş parçacığının ne zaman kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="13623-111">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="13623-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="13623-112">İş parçacıklarını oluşturmayı, başlatmayı, duraklatmayı, sürdürmeyi ve iptal etmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="13623-113">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="13623-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="13623-114">Eşitleme düzeylerini, kilitlenmeleri ve yarış durumlarını ve diğer iş parçacığı sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="13623-115">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="13623-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="13623-116">İş parçacıklarının etkinliklerini ve farklı iş parçacıklarında erişilen nesnelerin verilerini eşleştirmek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıkları için bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="13623-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13623-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="13623-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="13623-118">Yönetilen iş parçacıklarını kullanma ve eşitleme için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="13623-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="13623-119">Birden çok iş parçacığı ile kullanım için güvenli olan koleksiyon sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="13623-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="13623-120">Eşzamanlı işleme görevlerinin oluşturulması ve zamanlanması için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="13623-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13623-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="13623-121">Related Sections</span></span>  
 [<span data-ttu-id="13623-122">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="13623-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="13623-123">Uygulama etki alanlarına ve bunların ortak dil altyapısı tarafından kullanımına ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="13623-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="13623-124">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="13623-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="13623-125">Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="13623-126">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="13623-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="13623-127">.NET 'te zaman uyumsuz programlama için önerilen modele genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="13623-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="13623-128">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="13623-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="13623-129">Temsilcilerin yerleşik özellikleri kullanılarak iş parçacığı havuzu iş parçacıklarında yöntemlerin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="13623-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="13623-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="13623-131">Uygulamalarda birden çok iş parçacığının kullanımını kolaylaştıran paralel programlama kitaplıklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="13623-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="13623-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="13623-133">Birden çok işlemcinin avantajlarından yararlanmak için sorguları paralel olarak çalıştırmaya yönelik bir sistem açıklar.</span><span class="sxs-lookup"><span data-stu-id="13623-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
