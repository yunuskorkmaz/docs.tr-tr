---
title: Yönetilen İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: c5ca102dc98e50067d39d2f0c51a6ff75e342e9f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588662"
---
# <a name="managed-threading"></a><span data-ttu-id="144ac-102">Yönetilen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="144ac-102">Managed Threading</span></span>
<span data-ttu-id="144ac-103">İster bir işlemciye veya birkaç işlemciye sahip bilgisayarlar için geliştiriyor olun, uygulamanız şu anda başka bir iş yapıyor olsa bile, uygulamanızın kullanıcıyla en duyarlı etkileşimi sağlamasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="144ac-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="144ac-104">Birden çok yürütme iş parçacığı kullanmak, uygulamanızın kullanıcıya yanıt vermesini sağlamanın ve aynı zamanda kullanıcı olayları arasında ve hatta sırasında işlemciyi kullanmanın en güçlü yollarından biridir.</span><span class="sxs-lookup"><span data-stu-id="144ac-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="144ac-105">Bu bölümde iş parçacığı temel kavramları tanıtırken, yönetilen iş parçacığı kavramları ve yönetilen iş parçacığı kullanarak odaklanır.</span><span class="sxs-lookup"><span data-stu-id="144ac-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="144ac-106">.NET Framework 4 ile başlayarak, çok iş parçacığı programlama <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> büyük ölçüde ve sınıflar, [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)ile basitleştirilmiş, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanında yeni eşzamanlı toplama sınıfları ve iş parçacığı yerine görev kavramına dayalı yeni bir programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="144ac-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="144ac-107">Daha fazla bilgi için [Bkz. Paralel Programlama.](../../../docs/standard/parallel-programming/index.md)</span><span class="sxs-lookup"><span data-stu-id="144ac-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="144ac-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="144ac-108">In This Section</span></span>  
 [<span data-ttu-id="144ac-109">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="144ac-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="144ac-110">Yönetilen iş parçacığına genel bir bakış sağlar ve birden çok iş parçacığının ne zaman kullanılacağını tartışır.</span><span class="sxs-lookup"><span data-stu-id="144ac-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="144ac-111">İş Parçacığı ve İş Parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="144ac-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="144ac-112">İş iş parçacığı oluşturma, başlatma, duraklatma, devam etme ve iptal etme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="144ac-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="144ac-113">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="144ac-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="144ac-114">Eşitleme düzeylerini, kilitlenmeleri ve yarış koşullarını nasıl önleyebildiğini ve diğer iş parçacığı sorunlarını tartışır.</span><span class="sxs-lookup"><span data-stu-id="144ac-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="144ac-115">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="144ac-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="144ac-116">İş parçacıklarının etkinliklerini ve farklı iş parçacıklarında erişilen nesnelerin verilerini eşitlemek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıklarına genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="144ac-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="144ac-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="144ac-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="144ac-118">Yönetilen iş parçacıklarını kullanmak ve eşitlemek için sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="144ac-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="144ac-119">Birden çok iş parçacığı ile kullanım için güvenli toplama sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="144ac-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="144ac-120">Eşzamanlı işleme görevleri oluşturmak ve zamanletmek için sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="144ac-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="144ac-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="144ac-121">Related Sections</span></span>  
 [<span data-ttu-id="144ac-122">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="144ac-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="144ac-123">Uygulama etki alanlarına ve Bunların Ortak Dil Altyapısı tarafından kullanımına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="144ac-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="144ac-124">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="144ac-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="144ac-125">Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.</span><span class="sxs-lookup"><span data-stu-id="144ac-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="144ac-126">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="144ac-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="144ac-127">.NET'te eşzamanlı programlama için önerilen desenin genel görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="144ac-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="144ac-128">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="144ac-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="144ac-129">Temsilcilerin yerleşik özelliklerini kullanarak iş parçacığı havuzu iş parçacıklarındaki yöntemleri nasıl çağırılanın açıklar.</span><span class="sxs-lookup"><span data-stu-id="144ac-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="144ac-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="144ac-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="144ac-131">Uygulamalarda birden çok iş parçacığı kullanımını basitleştiren paralel programlama kitaplıklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="144ac-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="144ac-132">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="144ac-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="144ac-133">Birden çok işlemciden yararlanmak için sorguları paralel olarak çalıştırmak için bir sistem açıklar.</span><span class="sxs-lookup"><span data-stu-id="144ac-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
