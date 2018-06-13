---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir yöntem nasıl olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9d612186e1051644e8d4ae9476b8fafd811deb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567347"
---
# <a name="async-overview"></a><span data-ttu-id="81e7f-103">Zaman uyumsuz genel bakış</span><span class="sxs-lookup"><span data-stu-id="81e7f-103">Async Overview</span></span>

<span data-ttu-id="81e7f-104">Değil kısa süre önce uygulamaları daha hızlı yalnızca daha yeni bir bilgisayarı veya sunucuyu ve sonra bu eğilim satın durduruldu.</span><span class="sxs-lookup"><span data-stu-id="81e7f-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="81e7f-105">Aslında, ters.</span><span class="sxs-lookup"><span data-stu-id="81e7f-105">In fact, it reversed.</span></span> <span data-ttu-id="81e7f-106">Cep telefonları görünen 1 ghz tek çekirdek ARM yongaları ve sunucu iş yükleri için sanal makineleri geçiş yaptı.</span><span class="sxs-lookup"><span data-stu-id="81e7f-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="81e7f-107">Kullanıcılar hala yanıt veren UI ve işletme sahipleri kendi iş ölçeklendirme sunucuları istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="81e7f-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="81e7f-108">Mobil geçişi ve Bulut ve internet'e bağlı bir popülasyonunu > 3B kullanıcıların yeni bir yazılım desenleri kümesi ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="81e7f-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="81e7f-109">İstemci uygulamaları her zaman açık her zaman bağlı ve yüksek uygulama mağazası derecelendirmeleri ile (örneğin, dokunma) kullanıcı etkileşimi sürekli duyarlı olması beklenen!</span><span class="sxs-lookup"><span data-stu-id="81e7f-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="81e7f-110">Hizmetleri düzgün biçimde yukarı ve aşağı doğru ölçeklendirme tarafından artışlarını trafiğinin beklenir.</span><span class="sxs-lookup"><span data-stu-id="81e7f-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="81e7f-111">Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="81e7f-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="81e7f-112">.NET uygulamaları ve Hizmetleri için esnek ve kullanımı kolay, dil düzeyi zaman uyumsuz programlama modelleri C#, VB ve F # ile esnek olmasını yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="81e7f-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="81e7f-113">Neden zaman uyumsuz kod yazmayı?</span><span class="sxs-lookup"><span data-stu-id="81e7f-113">Why Write Async Code?</span></span>

<span data-ttu-id="81e7f-114">Modern uygulamalar dosya ve ağ g/ç yoğun olarak kullanımını olun.</span><span class="sxs-lookup"><span data-stu-id="81e7f-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="81e7f-115">G/ç API'leri geleneksel olarak varsayılan olarak, blok öğrenmek ve zor desenleri kullanmak istemediğiniz sürece zayıf kullanıcı deneyimleri ve donanım kullanımı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="81e7f-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="81e7f-116">Görev tabanlı zaman uyumsuz API'leri ve dil düzeyi zaman uyumsuz programlama modeli öğrenmek için birkaç yeni kavram varsayılan zaman uyumsuz yürütme yapmadan bu model, ters çevir.</span><span class="sxs-lookup"><span data-stu-id="81e7f-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="81e7f-117">Zaman uyumsuz kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="81e7f-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="81e7f-118">G/ç istekleri döndürmek beklenirken daha fazla isteği işlemek için iş parçacığı oluşturan tarafından daha fazla sunucu isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="81e7f-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="81e7f-119">G/ç istekleri için beklenirken UI etkileşim için iş parçacığı oluşturan ve uzun süre çalışan iş diğer CPU çekirdekleri geçiş göre daha iyi yanıt olarak Uı'lar sağlar.</span><span class="sxs-lookup"><span data-stu-id="81e7f-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="81e7f-120">Birçok yeni .NET API'lerini uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="81e7f-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="81e7f-121">. NET'te zaman uyumsuz kod yazmaya kolaydır!</span><span class="sxs-lookup"><span data-stu-id="81e7f-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="81e7f-122">Sonraki adım nedir?</span><span class="sxs-lookup"><span data-stu-id="81e7f-122">What's next?</span></span>

<span data-ttu-id="81e7f-123">Daha fazla bilgi için bkz: [zaman uyumsuz derinlemesine](async-in-depth.md) konu.</span><span class="sxs-lookup"><span data-stu-id="81e7f-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="81e7f-124">[Zaman uyumsuz programlama desenleri](/asynchronous-programming-patterns/index.md) konu .NET içinde desteklenen üç zaman uyumsuz programlama desenleri genel bir bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="81e7f-124">The [Asynchronous Programming Patterns](/asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
-   <span data-ttu-id="81e7f-125">[Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="81e7f-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="81e7f-126">[Olay tabanlı zaman uyumsuz desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="81e7f-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="81e7f-127">[Görev tabanlı zaman uyumsuz desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme projeleri için önerilir)</span><span class="sxs-lookup"><span data-stu-id="81e7f-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="81e7f-128">Görev tabanlı önerilen programlama modeli hakkında daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz programlama](parallel-programming/task-based-asynchronous-programming.md) konu.</span><span class="sxs-lookup"><span data-stu-id="81e7f-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
