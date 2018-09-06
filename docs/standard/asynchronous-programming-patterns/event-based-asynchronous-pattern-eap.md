---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be4935d74affa227386aa6c63dad13e7e2f7d3dd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877482"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="e4f0b-102">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="e4f0b-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="e4f0b-103">İstemci kodu zaman uyumsuz özelliklerini göstermek için çeşitli yollarla vardır.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="e4f0b-104">Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranış sunmak sınıflar için bir yol kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4f0b-105">.NET Framework 4 ile başlayarak, görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="e4f0b-106">Daha fazla bilgi için [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz desen (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="e4f0b-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e4f0b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e4f0b-107">In This Section</span></span>

 [<span data-ttu-id="e4f0b-108">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4f0b-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="e4f0b-109">Açıklayan nasıl olay tabanlı zaman uyumsuz desen çok iş parçacıklı uygulamalar avantajları pek çok iş parçacıklı tasarımında devralınan karmaşık sorunların gizleyerek kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="e4f0b-110">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="e4f0b-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-111">Zaman uyumsuz özellikler sahip bir sınıf paketlemek için standartlaştırılmış bir yol açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="e4f0b-112">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e4f0b-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-113">Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="e4f0b-114">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e4f0b-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-115">Ne zaman yerine olay tabanlı zaman uyumsuz desen uygulamak seçmelidir olmadığının nasıl belireneceğini açıklar <xref:System.IAsyncResult> düzeni temsil ettiği [zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="e4f0b-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="e4f0b-116">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="e4f0b-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-117">Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="e4f0b-118">Yardımcı sınıflarından kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı bileşen herhangi bir uygulama modeli altında düzgün şekilde çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="e4f0b-119">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="e4f0b-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-120">Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen kullanan bir istemci oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="e4f0b-121">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e4f0b-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e4f0b-122">Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e4f0b-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e4f0b-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="e4f0b-124">Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="e4f0b-125">Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="e4f0b-126">Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşen ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4f0b-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e4f0b-127">Related Sections</span></span>

 [<span data-ttu-id="e4f0b-128">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="e4f0b-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="e4f0b-129">Zaman uyumsuz ve paralel işlemler için bir programlama modeli açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="e4f0b-130">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4f0b-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="e4f0b-131">. NET'te çok iş parçacıklı özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f0b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f0b-132">See also</span></span>

- [<span data-ttu-id="e4f0b-133">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="e4f0b-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)  
- [<span data-ttu-id="e4f0b-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e4f0b-134">Events</span></span>](../events/index.md)  
- [<span data-ttu-id="e4f0b-135">Zaman uyumsuz programlama desenleri</span><span class="sxs-lookup"><span data-stu-id="e4f0b-135">Asynchronous Programming Design Patterns</span></span>](index.md)
