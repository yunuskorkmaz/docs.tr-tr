---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eş zamanlı işlemleri işlemek kolaylaştırıyor önemli bir tekniktir nasıl olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9084da80ff400bf99fc8641c69bc38c805d039a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627911"
---
# <a name="async-overview"></a><span data-ttu-id="b6018-103">Zaman uyumsuz genel bakış</span><span class="sxs-lookup"><span data-stu-id="b6018-103">Async Overview</span></span>

<span data-ttu-id="b6018-104">Bu nedenle zamanlara kadar uygulamaları daha hızlı yalnızca daha yeni bir PC veya sunucuyu ve ardından ilgili eğilim satın alarak durduruldu.</span><span class="sxs-lookup"><span data-stu-id="b6018-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="b6018-105">Aslında, ters.</span><span class="sxs-lookup"><span data-stu-id="b6018-105">In fact, it reversed.</span></span> <span data-ttu-id="b6018-106">Cep telefonları, 1 ghz tek çekirdek ARM görünen yongaları ve sunucu iş yükleri Vm'lere geçti.</span><span class="sxs-lookup"><span data-stu-id="b6018-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="b6018-107">Kullanıcılar hala duyarlı kullanıcı Arabirimi ve işletme sahipleri ile işlerini ölçeklendirmeyi sunucuları istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="b6018-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="b6018-108">Geçiş mobil ve Bulut ve İnternet'e bağlı bir popülasyonunu > 3B kullanıcılar yeni bir yazılım desenleri kümesi ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="b6018-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="b6018-109">İstemci uygulamalar her zaman açık her zaman bağlı ve sürekli etkileşime yanıt vermesini kullanıcı (örneğin, dokunma) ile yüksek app store derecelendirme olması bekleniyor!</span><span class="sxs-lookup"><span data-stu-id="b6018-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="b6018-110">Hizmetler düzgün biçimde yukarı ve aşağı ölçeklendirme tarafından trafiğindeki ani artışları idare beklenir.</span><span class="sxs-lookup"><span data-stu-id="b6018-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="b6018-111">Zaman uyumsuz programlama, engelleme g/ç ve birden çok çekirdek eş zamanlı işlemleri işlemek kolaylaştırıyor önemli bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="b6018-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="b6018-112">.NET uygulamaları ve Hizmetleri için hızlı ve kullanımı kolay, dil düzeyinde zaman uyumsuz programlama modelleri ile elastik yeteneği sağlar C#, VB ve F#.</span><span class="sxs-lookup"><span data-stu-id="b6018-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="b6018-113">Zaman uyumsuz kodu neden yazılsın mı?</span><span class="sxs-lookup"><span data-stu-id="b6018-113">Why Write Async Code?</span></span>

<span data-ttu-id="b6018-114">Modern uygulamalar, dosya ve ağ g/ç yoğun olarak kullanımını olun.</span><span class="sxs-lookup"><span data-stu-id="b6018-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="b6018-115">G/ç API'leri varsayılan olarak, geleneksel blok öğrenmek ve zorlu desenleri kullanmak istemediğiniz sürece kötü kullanıcı deneyimleri ve donanım kullanımı sonucu.</span><span class="sxs-lookup"><span data-stu-id="b6018-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="b6018-116">Görev tabanlı zaman uyumsuz API'leri ve dil düzeyi zaman uyumsuz programlama modeli varsayılan öğrenmek için bazı yeni kavramlar ile zaman uyumsuz yürütme yapmadan bu model, ters çevir.</span><span class="sxs-lookup"><span data-stu-id="b6018-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="b6018-117">Zaman uyumsuz kod, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b6018-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="b6018-118">Döndürülecek g/ç istekleri için beklenirken daha fazla isteği işlemek için iş parçacığı oluşturan tarafından daha fazla sunucu isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="b6018-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="b6018-119">Kullanıcı Arabirimi etkileşimi için g/ç isteği beklerken iş parçacığı oluşturan ve diğer CPU çekirdekleri için uzun süre çalışan iş geçiş göre daha hızlı yanıt verdiğini kullanıcı arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6018-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="b6018-120">Birçok yeni .NET API'lerini uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="b6018-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="b6018-121">. NET'te zaman uyumsuz kod yazmayı kolaydır!</span><span class="sxs-lookup"><span data-stu-id="b6018-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="b6018-122">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="b6018-122">What's next?</span></span>

<span data-ttu-id="b6018-123">Daha fazla bilgi için [zaman uyumsuz derinlemesine](async-in-depth.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b6018-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="b6018-124">[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) konu,. NET'te desteklenen üç zaman uyumsuz programlama desenleri için genel bir bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="b6018-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="b6018-125">[Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="b6018-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="b6018-126">[Olay tabanlı zaman uyumsuz desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="b6018-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="b6018-127">[Görev tabanlı zaman uyumsuz desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme projeleri için önerilir)</span><span class="sxs-lookup"><span data-stu-id="b6018-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="b6018-128">Önerilen görev-tabanlı programlama modeli hakkında daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b6018-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
