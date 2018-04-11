---
title: Zaman uyumsuz genel bakış
description: Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir yöntem nasıl olduğunu öğrenin.
keywords: .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2dddc21dfb124fe97c397a156743981a67e4037
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="async-overview"></a><span data-ttu-id="796ca-104">Zaman uyumsuz genel bakış</span><span class="sxs-lookup"><span data-stu-id="796ca-104">Async Overview</span></span>

<span data-ttu-id="796ca-105">Değil kısa süre önce uygulamaları daha hızlı yalnızca daha yeni bir bilgisayarı veya sunucuyu ve sonra bu eğilim satın durduruldu.</span><span class="sxs-lookup"><span data-stu-id="796ca-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="796ca-106">Aslında, ters.</span><span class="sxs-lookup"><span data-stu-id="796ca-106">In fact, it reversed.</span></span> <span data-ttu-id="796ca-107">Cep telefonları görünen 1 ghz tek çekirdek ARM yongaları ve sunucu iş yükleri için sanal makineleri geçiş yaptı.</span><span class="sxs-lookup"><span data-stu-id="796ca-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="796ca-108">Kullanıcılar hala yanıt veren UI ve işletme sahipleri kendi iş ölçeklendirme sunucuları istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="796ca-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="796ca-109">Mobil geçişi ve Bulut ve internet'e bağlı bir popülasyonunu > 3B kullanıcıların yeni bir yazılım desenleri kümesi ile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="796ca-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="796ca-110">İstemci uygulamaları her zaman açık her zaman bağlı ve yüksek uygulama mağazası derecelendirmeleri ile (örneğin, dokunma) kullanıcı etkileşimi sürekli duyarlı olması beklenen!</span><span class="sxs-lookup"><span data-stu-id="796ca-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="796ca-111">Hizmetleri düzgün biçimde yukarı ve aşağı doğru ölçeklendirme tarafından artışlarını trafiğinin beklenir.</span><span class="sxs-lookup"><span data-stu-id="796ca-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="796ca-112">Zaman uyumsuz programlama engelleme g/ç ve birden çok çekirdek eşzamanlı işlem işlemek basitleştirir anahtar bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="796ca-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="796ca-113">.NET uygulamaları ve Hizmetleri için esnek ve kullanımı kolay, dil düzeyi zaman uyumsuz programlama modelleri C#, VB ve F # ile esnek olmasını yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="796ca-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="796ca-114">Neden zaman uyumsuz kod yazmayı?</span><span class="sxs-lookup"><span data-stu-id="796ca-114">Why Write Async Code?</span></span>

<span data-ttu-id="796ca-115">Modern uygulamalar dosya ve ağ g/ç yoğun olarak kullanımını olun.</span><span class="sxs-lookup"><span data-stu-id="796ca-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="796ca-116">G/ç API'leri geleneksel olarak varsayılan olarak, blok öğrenmek ve zor desenleri kullanmak istemediğiniz sürece zayıf kullanıcı deneyimleri ve donanım kullanımı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="796ca-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="796ca-117">Görev tabanlı zaman uyumsuz API'leri ve dil düzeyi zaman uyumsuz programlama modeli öğrenmek için birkaç yeni kavram varsayılan zaman uyumsuz yürütme yapmadan bu model, ters çevir.</span><span class="sxs-lookup"><span data-stu-id="796ca-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="796ca-118">Zaman uyumsuz kod aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="796ca-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="796ca-119">G/ç istekleri döndürmek beklenirken daha fazla isteği işlemek için iş parçacığı oluşturan tarafından daha fazla sunucu isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="796ca-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="796ca-120">G/ç istekleri için beklenirken UI etkileşim için iş parçacığı oluşturan ve uzun süre çalışan iş diğer CPU çekirdekleri geçiş göre daha iyi yanıt olarak Uı'lar sağlar.</span><span class="sxs-lookup"><span data-stu-id="796ca-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="796ca-121">Birçok yeni .NET API'lerini uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="796ca-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="796ca-122">. NET'te zaman uyumsuz kod yazmaya kolaydır!</span><span class="sxs-lookup"><span data-stu-id="796ca-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="796ca-123">Sonraki adım nedir?</span><span class="sxs-lookup"><span data-stu-id="796ca-123">What's next?</span></span>

<span data-ttu-id="796ca-124">Zaman uyumsuz kavramları ve programlama derinlemesine bir bakış için bkz: [zaman uyumsuz derinlemesine](async-in-depth.md) ve [görev tabanlı zaman uyumsuz programlama](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="796ca-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
