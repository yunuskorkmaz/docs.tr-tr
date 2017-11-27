---
title: "Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a26f6750f68609b40e6917fc5b257e43d95c3c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="b2278-102">Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama</span><span class="sxs-lookup"><span data-stu-id="b2278-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="b2278-103">Bir istemci kodu için zaman uyumsuz özellikler kullanıma sunmak için çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="b2278-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="b2278-104">Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranışı sunmak sınıflar için önerilen yol önerir.</span><span class="sxs-lookup"><span data-stu-id="b2278-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2278-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b2278-105">In This Section</span></span>  
 [<span data-ttu-id="b2278-106">Olay tabanlı zaman uyumsuz desene genel bakış</span><span class="sxs-lookup"><span data-stu-id="b2278-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="b2278-107">Nasıl olay tabanlı zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2278-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="b2278-108">Olay tabanlı zaman uyumsuz deseni uygulama</span><span class="sxs-lookup"><span data-stu-id="b2278-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="b2278-109">Zaman uyumsuz özellikler olan bir sınıfı paketlemek için standartlaştırılmış biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2278-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="b2278-110">Olay tabanlı zaman uyumsuz desen uygulamak için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b2278-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="b2278-111">Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2278-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="b2278-112">Olay tabanlı zaman uyumsuz desen uygulamak karar verme</span><span class="sxs-lookup"><span data-stu-id="b2278-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="b2278-113">Yerine olay tabanlı zaman uyumsuz desen uygulamak seçtiğinizde belirlemek açıklar <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="b2278-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="b2278-114">İzlenecek yol: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama</span><span class="sxs-lookup"><span data-stu-id="b2278-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="b2278-115">Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2278-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="b2278-116">Yardımcı sınıfları kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı altında herhangi bir uygulama modeli bileşeni düzgün çalıştığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2278-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="b2278-117">Nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bileşenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b2278-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="b2278-118">Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2278-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b2278-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b2278-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="b2278-120">Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b2278-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="b2278-121">Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b2278-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b2278-122">Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşeni ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b2278-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2278-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2278-123">See Also</span></span>  
 [<span data-ttu-id="b2278-124">Yönetilen iş parçacığı oluşturma en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b2278-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="b2278-125">Olayları</span><span class="sxs-lookup"><span data-stu-id="b2278-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="b2278-126">Bileşenleri çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="b2278-126">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="b2278-127">Olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="b2278-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
