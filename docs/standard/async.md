---
title: Async Genel Bakış
description: Async programlamanın, engelleme G/Ç ve birden çok çekirdekteki eşzamanlı işlemleri işlemeyi kolaylaştıran önemli bir teknik olduğunu öğrenin.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159734"
---
# <a name="async-overview"></a><span data-ttu-id="e184f-103">Async Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e184f-103">Async Overview</span></span>

<span data-ttu-id="e184f-104">O kadar uzun zaman önce, uygulamalar sadece yeni bir PC veya sunucu satın alarak daha hızlı var ve daha sonra bu eğilim durdu.</span><span class="sxs-lookup"><span data-stu-id="e184f-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="e184f-105">Aslında, tersine döndü.</span><span class="sxs-lookup"><span data-stu-id="e184f-105">In fact, it reversed.</span></span> <span data-ttu-id="e184f-106">Cep telefonları 1ghz tek çekirdekli ARM yongaları ve sunucu iş yükleri VMs geçişli ile ortaya çıktı.</span><span class="sxs-lookup"><span data-stu-id="e184f-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="e184f-107">Kullanıcılar hala duyarlı Kullanıcı Bira ve işletme sahipleri kendi iş ile ölçeksunucular istiyorum istiyorum.</span><span class="sxs-lookup"><span data-stu-id="e184f-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="e184f-108">Mobil ve buluta geçiş ve >3B kullanıcılarının internete bağlı nüfusu yeni bir yazılım kalıpları kümesiile sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="e184f-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="e184f-109">İstemci uygulamalarının her zaman açık, her zaman bağlı ve yüksek uygulama mağazası derecelendirmeleriyle kullanıcı etkileşimine (örneğin dokunma) sürekli yanıt vermesini bekler!</span><span class="sxs-lookup"><span data-stu-id="e184f-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="e184f-110">Hizmetlerin, incelikle yukarı ve aşağı ölçeklendirerek trafikteki ani artışlarla başa çıkaması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="e184f-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="e184f-111">Async programlama, engelleme G/Ç ve birden çok çekirdek teki eşzamanlı işlemleri işlemeyi kolaylaştıran önemli bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="e184f-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="e184f-112">.NET, C#, Visual Basic ve F#'da kullanımı kolay, dil düzeyinde asynchronous programlama modelleri ile uygulamaların ve hizmetlerin duyarlı ve esnek olması için gereken yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e184f-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="e184f-113">Neden Async Kodu Yaz?</span><span class="sxs-lookup"><span data-stu-id="e184f-113">Why Write Async Code?</span></span>

<span data-ttu-id="e184f-114">Modern uygulamalar dosya ve ağ G/Ç'yi kapsamlı bir şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="e184f-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="e184f-115">G/Ç API'leri varsayılan olarak engellenir ve zorlu desenleri öğrenmek ve kullanmak istemediğiniz sürece kötü kullanıcı deneyimleri ve donanım kullanımı yla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e184f-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="e184f-116">Görev tabanlı async API'leri ve dil düzeyindeki asynchronous programlama modeli bu modeli tersine çevirerek, async yürütmeyi öğrenmek için birkaç yeni kavramla varsayılan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e184f-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="e184f-117">Async kodu aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e184f-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="e184f-118">G/Ç isteklerinin geri dönmesini beklerken daha fazla isteği işlemek için iş parçacıkları vererek daha fazla sunucu isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="e184f-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="e184f-119">G/Ç isteklerini beklerken ve uzun süren çalışmaları diğer CPU çekirdeklerine geçirerek Kullanıcı Araları'nın Kullanıcı Arabirimi etkileşimine iş parçacığı vererek daha duyarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e184f-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="e184f-120">Yeni .NET API'lerinin çoğu eşzamanlıdır.</span><span class="sxs-lookup"><span data-stu-id="e184f-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="e184f-121">.NET'te async kodu yazmak kolaydır!</span><span class="sxs-lookup"><span data-stu-id="e184f-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="e184f-122">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="e184f-122">What's next?</span></span>

<span data-ttu-id="e184f-123">Daha fazla bilgi [için, derinlemesine konu yla Ilgili Async konusuna](async-in-depth.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="e184f-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="e184f-124">[Asynchronous Programlama Desenleri](asynchronous-programming-patterns/index.md) konusu ,NET'te desteklenen üç eşzamanlı programlama deleline genel bir bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="e184f-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="e184f-125">[Eşzamanlı Programlama Modeli (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="e184f-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="e184f-126">[Olay tabanlı Eşzamanlı Desen (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (eski)</span><span class="sxs-lookup"><span data-stu-id="e184f-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="e184f-127">[Görev tabanlı Eşzamanlı Desen (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (yeni geliştirme için önerilir)</span><span class="sxs-lookup"><span data-stu-id="e184f-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="e184f-128">Önerilen görev tabanlı programlama modeli hakkında daha fazla bilgi için [Görev tabanlı asynchronous programlama](parallel-programming/task-based-asynchronous-programming.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e184f-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
