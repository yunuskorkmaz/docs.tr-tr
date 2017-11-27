---
title: "Olay Tabanlı Zaman Uyumsuz Desen (EAP)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b5f242b9586c4ea3b045daf8f10b84127b81085
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="bace5-102">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="bace5-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="bace5-103">Bir istemci kodu için zaman uyumsuz özellikler kullanıma sunmak için çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="bace5-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="bace5-104">Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranışı sunmak sınıflar için bir yol önerir.</span><span class="sxs-lookup"><span data-stu-id="bace5-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bace5-105">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="bace5-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="bace5-106">Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="bace5-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bace5-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bace5-107">In This Section</span></span>  
 [<span data-ttu-id="bace5-108">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="bace5-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="bace5-109">Nasıl olay tabanlı zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="bace5-110">Olay tabanlı zaman uyumsuz deseni uygulama</span><span class="sxs-lookup"><span data-stu-id="bace5-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bace5-111">Zaman uyumsuz özellikler olan bir sınıfı paketlemek için standartlaştırılmış biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bace5-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="bace5-112">Olay tabanlı zaman uyumsuz desen uygulamak için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bace5-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bace5-113">Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="bace5-114">Olay tabanlı zaman uyumsuz desen uygulamak karar verme</span><span class="sxs-lookup"><span data-stu-id="bace5-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bace5-115">Yerine olay tabanlı zaman uyumsuz desen uygulamak seçtiğinizde belirlemek açıklar <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="bace5-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="bace5-116">İzlenecek yol: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama</span><span class="sxs-lookup"><span data-stu-id="bace5-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bace5-117">Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bace5-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="bace5-118">Yardımcı sınıfları kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı altında herhangi bir uygulama modeli bileşeni düzgün çalıştığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bace5-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="bace5-119">Nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bileşenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="bace5-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bace5-120">Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bace5-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bace5-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="bace5-122">Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="bace5-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="bace5-123">Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="bace5-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="bace5-124">Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşeni ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="bace5-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bace5-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bace5-125">Related Sections</span></span>  
 [<span data-ttu-id="bace5-126">Görev paralel kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="bace5-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="bace5-127">Zaman uyumsuz ve paralel işlemleri için bir programlama modeli açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="bace5-128">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="bace5-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="bace5-129">.NET Framework'teki çoklu iş parçacığı özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="bace5-130">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="bace5-130">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="bace5-131">C# ve Visual Basic dillerde çoklu iş parçacığı özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="bace5-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bace5-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bace5-132">See Also</span></span>  
 [<span data-ttu-id="bace5-133">Yönetilen iş parçacığı oluşturma en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bace5-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="bace5-134">Olayları</span><span class="sxs-lookup"><span data-stu-id="bace5-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="bace5-135">Bileşenleri çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="bace5-135">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="bace5-136">Zaman uyumsuz programlama tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="bace5-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
