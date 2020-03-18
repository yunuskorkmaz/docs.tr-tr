---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: ee8c90d63478e444b7d25cb7cbb5c969963d7c63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130937"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="f9c7a-102">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="f9c7a-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="f9c7a-103">Eşiş özelliklerini istemci koduna maruz bırakmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="f9c7a-104">Olay tabanlı Asynchronous Pattern, sınıfların eşzamanlı davranış göstermesi için bir yol yazar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9c7a-105">.NET Framework 4'ten başlayarak, Görev Paralel Kitaplığı asynchronous ve paralel programlama için yeni bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="f9c7a-106">Daha fazla bilgi için [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [Görev Tabanlı Eşzamanlı Desen (TAP)](task-based-asynchronous-pattern-tap.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="f9c7a-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f9c7a-107">In This Section</span></span>

 [<span data-ttu-id="f9c7a-108">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9c7a-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="f9c7a-109">Olay tabanlı Asynchronous Deseni'nin, çok iş parçacığı tasarımının doğasında bulunan karmaşık sorunların çoğunu gizlerken çok iş parçacığı uygulamalarının avantajlarını nasıl kullanıma sundığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="f9c7a-110">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="f9c7a-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-111">Eşzamanlı özelliklere sahip bir sınıfı paketlemenin standartlaştırılmış yolunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="f9c7a-112">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f9c7a-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-113">Olay tabanlı Asynchronous Deseni'ne göre eşzamanlı özellikleri ortaya çıkarmak için gereksinimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="f9c7a-114">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f9c7a-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-115"><xref:System.IAsyncResult> [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen desen yerine Olay tabanlı Eşenkron Deseni'ni ne zaman uygulamanız gerektiğini nasıl belirleyeceğinizi açıklar</span><span class="sxs-lookup"><span data-stu-id="f9c7a-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="f9c7a-116">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="f9c7a-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-117">Olay tabanlı Asynchronous Deseni'ni uygulayan bir bileşenin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="f9c7a-118">Bileşenin herhangi bir uygulama modeli <xref:System.ComponentModel?displayProperty=nameWithType> altında doğru çalışmasını sağlayan ad alanından yardımcı sınıflar kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="f9c7a-119">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="f9c7a-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-120">Olay tabanlı Asynchronous Deseni'ni uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="f9c7a-121">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f9c7a-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="f9c7a-122">Olay tabanlı Asynchronous Deseni destekleyen bir bileşenin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9c7a-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f9c7a-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="f9c7a-124"><xref:System.ComponentModel.AsyncOperation> Sınıfı açıklar ve tüm üyelerine bağlantılar alalar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="f9c7a-125"><xref:System.ComponentModel.AsyncOperationManager> Sınıfı açıklar ve tüm üyelerine bağlantılar alalar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="f9c7a-126"><xref:System.ComponentModel.BackgroundWorker> Bileşeni açıklar ve tüm üyelerine bağlantılar vardır.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9c7a-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f9c7a-127">Related Sections</span></span>

 [<span data-ttu-id="f9c7a-128">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="f9c7a-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="f9c7a-129">Eşzamanlı ve paralel işlemler için bir programlama modelini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="f9c7a-130">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9c7a-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="f9c7a-131">.NET'te çok iş parçacığı özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c7a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9c7a-132">See also</span></span>

- [<span data-ttu-id="f9c7a-133">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f9c7a-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="f9c7a-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f9c7a-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="f9c7a-135">Asynchronous Programlama Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="f9c7a-135">Asynchronous Programming Design Patterns</span></span>](index.md)
