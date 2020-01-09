---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlamanın, birden çok çekirdekte g/ç ve eş zamanlı işlemleri engellemeyi doğrudan işlemesini sağlayan bir anahtar tekniği olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 1570909b7b416eff81dd90a936ff5ed10aad94f1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346080"
---
# <a name="async-overview"></a><span data-ttu-id="7cbde-103">Zaman uyumsuz genel bakış</span><span class="sxs-lookup"><span data-stu-id="7cbde-103">Async Overview</span></span>

<span data-ttu-id="7cbde-104">Bu kadar uzun bir süre önce, uygulamalar daha yeni bir BILGISAYAR veya sunucu satın alarak daha hızlı bir şekilde daha hızlı bir şekilde daha hızlı</span><span class="sxs-lookup"><span data-stu-id="7cbde-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="7cbde-105">Aslında tersine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="7cbde-105">In fact, it reversed.</span></span> <span data-ttu-id="7cbde-106">Cep telefonları, 1 GHz tek çekirdekli ARM yongalarını ve sunucu iş yüklerini VM 'lere geçti.</span><span class="sxs-lookup"><span data-stu-id="7cbde-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="7cbde-107">Kullanıcılar hala yanıt veren kullanıcı arabirimi ve işletme sahiplerinin işletmeyle ölçeklendirebilmesini istiyor.</span><span class="sxs-lookup"><span data-stu-id="7cbde-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="7cbde-108">Mobil ve buluta geçiş ve > 3B kullanıcıların Internet 'e bağlı bir popülasyonu, yeni bir yazılım desenleri kümesiyle sonuçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7cbde-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

- <span data-ttu-id="7cbde-109">İstemci uygulamalarının her zaman açık, her zaman bağlı ve sürekli olarak kullanıcı etkileşimine (örneğin, Touch) yüksek uygulama mağazası derecelendirmelerine sahip olması beklenir!</span><span class="sxs-lookup"><span data-stu-id="7cbde-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="7cbde-110">Hizmetin, trafiği yukarı ve aşağı doğru şekilde ölçeklendirerek, trafikte ani artışları işlemesi beklenir.</span><span class="sxs-lookup"><span data-stu-id="7cbde-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="7cbde-111">Zaman uyumsuz programlama, birden çok çekirdekte g/ç ve eş zamanlı işlemleri engellemeyi doğrudan işlemesini sağlayan temel bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="7cbde-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="7cbde-112">.NET,, Visual Basic ve C# F#' de kullanımı kolay, dil düzeyi zaman uyumsuz programlama modelleriyle uygulamalar ve hizmetler için yanıt verme ve elastik hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7cbde-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="7cbde-113">Zaman uyumsuz kod neden yazılır?</span><span class="sxs-lookup"><span data-stu-id="7cbde-113">Why Write Async Code?</span></span>

<span data-ttu-id="7cbde-114">Modern uygulamalar, dosya ve ağ g/ç 'nin kapsamlı bir şekilde kullanılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7cbde-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="7cbde-115">G/ç API 'Leri geleneksel olarak varsayılan olarak engellenerek, zorlu desenler öğrenmek ve kullanmak istemediğiniz müddetçe kötü kullanıcı deneyimleri ve donanım kullanımı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7cbde-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="7cbde-116">Görev tabanlı zaman uyumsuz API 'Ler ve dil düzeyi zaman uyumsuz programlama modeli, bu modeli tersine çevirir ve daha fazla yeni kavram ile varsayılan olarak zaman uyumsuz yürütmeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="7cbde-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="7cbde-117">Zaman uyumsuz kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7cbde-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="7cbde-118">G/ç isteklerinin dönmesi beklenirken daha fazla isteği işlemek için iş parçacıkları sunarak daha fazla sunucu isteği işler.</span><span class="sxs-lookup"><span data-stu-id="7cbde-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="7cbde-119">G/ç isteklerini beklerken ve uzun süre çalışan işleri diğer CPU çekirdeğlerine geçirerek Uıto 'ın Kullanıcı arabirimi etkileşimine yanıt vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cbde-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="7cbde-120">Daha yeni .NET API 'Lerinin birçoğu zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="7cbde-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="7cbde-121">.NET ' te zaman uyumsuz kod yazmak kolaydır!</span><span class="sxs-lookup"><span data-stu-id="7cbde-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="7cbde-122">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="7cbde-122">What's next?</span></span>

<span data-ttu-id="7cbde-123">Daha fazla bilgi için bkz. [zaman uyumsuz ayrıntılı](async-in-depth.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="7cbde-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="7cbde-124">[Zaman uyumsuz programlama desenleri](asynchronous-programming-patterns/index.md) konusu, .net 'te desteklenen üç zaman uyumsuz programlama desenlerine genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="7cbde-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="7cbde-125">[Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="7cbde-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="7cbde-126">[Olay tabanlı zaman uyumsuz model (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="7cbde-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="7cbde-127">[Görev tabanlı zaman uyumsuz model (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme için önerilir)</span><span class="sxs-lookup"><span data-stu-id="7cbde-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="7cbde-128">Önerilen görev tabanlı programlama modeli hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="7cbde-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
