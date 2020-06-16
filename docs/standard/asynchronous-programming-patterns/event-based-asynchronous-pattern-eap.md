---
title: Olay Tabanlı Zaman Uyumsuz Desen (EAP)
description: Uygulama, en iyi uygulamalar, EAP istemcisi uygulama ve daha fazlası gibi .NET 'teki olay tabanlı zaman uyumsuz model (EAP) hakkında makalelerin bağlantılarını inceleyin.
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 03b4d914d72b96b882c774565654c022b145b5f2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768878"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="bf33d-103">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="bf33d-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="bf33d-104">İstemci kodunda zaman uyumsuz özellikleri açığa çıkarmak için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="bf33d-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="bf33d-105">Olay tabanlı zaman uyumsuz model, sınıfların zaman uyumsuz davranışı sunmak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf33d-106">.NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-106">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="bf33d-107">Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="bf33d-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="bf33d-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bf33d-108">In This Section</span></span>

 [<span data-ttu-id="bf33d-109">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bf33d-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="bf33d-110">Çok iş parçacıklı tasarımda bulunan karmaşık sorunların çoğunu gizleyerek, olay tabanlı zaman uyumsuz düzenin çoklu iş parçacıklı uygulamaların avantajlarından nasıl yararlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="bf33d-111">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="bf33d-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-112">Zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standartlaştırılmış bir yol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="bf33d-113">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf33d-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-114">Zaman uyumsuz özellikleri olay tabanlı zaman uyumsuz düzene göre gösterme gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="bf33d-115">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="bf33d-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-116"><xref:System.IAsyncResult> [Zaman uyumsuz programlama MODELI (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen model yerine olay tabanlı zaman uyumsuz model uygulamayı ne zaman kullanacağınızı belirlemeyi açıklar</span><span class="sxs-lookup"><span data-stu-id="bf33d-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="bf33d-117">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="bf33d-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-118">Olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="bf33d-119">Bu, <xref:System.ComponentModel?displayProperty=nameWithType> bileşenin herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak üzere ad alanından yardımcı sınıflar kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bf33d-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="bf33d-120">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="bf33d-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-121">Olay tabanlı zaman uyumsuz model uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="bf33d-122">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="bf33d-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="bf33d-123">Olay tabanlı zaman uyumsuz stili destekleyen bir bileşenin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bf33d-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bf33d-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="bf33d-125">Sınıfını açıklar <xref:System.ComponentModel.AsyncOperation> ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="bf33d-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="bf33d-126">Sınıfını açıklar <xref:System.ComponentModel.AsyncOperationManager> ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="bf33d-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="bf33d-127">Bileşenini açıklar <xref:System.ComponentModel.BackgroundWorker> ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="bf33d-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf33d-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bf33d-128">Related Sections</span></span>

 [<span data-ttu-id="bf33d-129">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="bf33d-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="bf33d-130">Zaman uyumsuz ve paralel işlemler için bir programlama modeli tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="bf33d-131">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf33d-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="bf33d-132">.NET 'teki çoklu iş parçacığı özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bf33d-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf33d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf33d-133">See also</span></span>

- [<span data-ttu-id="bf33d-134">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="bf33d-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="bf33d-135">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf33d-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="bf33d-136">Zaman uyumsuz programlama tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="bf33d-136">Asynchronous Programming Design Patterns</span></span>](index.md)
