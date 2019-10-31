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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130937"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="17059-102">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="17059-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="17059-103">İstemci kodunda zaman uyumsuz özellikleri açığa çıkarmak için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="17059-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="17059-104">Olay tabanlı zaman uyumsuz model, sınıfların zaman uyumsuz davranışı sunmak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="17059-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17059-105">.NET Framework 4 ' den başlayarak, görev paralel kitaplığı, zaman uyumsuz ve paralel programlama için yeni bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="17059-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="17059-106">Daha fazla bilgi için bkz. [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [görev tabanlı zaman uyumsuz model (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="17059-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="17059-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="17059-107">In This Section</span></span>

 [<span data-ttu-id="17059-108">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17059-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="17059-109">Çok iş parçacıklı tasarımda bulunan karmaşık sorunların çoğunu gizleyerek, olay tabanlı zaman uyumsuz düzenin çoklu iş parçacıklı uygulamaların avantajlarından nasıl yararlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="17059-110">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="17059-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-111">Zaman uyumsuz özellikleri olan bir sınıfı paketlemek için standartlaştırılmış bir yol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17059-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="17059-112">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="17059-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-113">Zaman uyumsuz özellikleri olay tabanlı zaman uyumsuz düzene göre gösterme gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="17059-114">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="17059-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-115">[Zaman uyumsuz programlama modeli (APM)](asynchronous-programming-model-apm.md) tarafından temsil edilen <xref:System.IAsyncResult> modeli yerine olay tabanlı zaman uyumsuz model uygulamayı ne zaman kullanacağınızı nasıl belirleyebileceğinizi açıklar</span><span class="sxs-lookup"><span data-stu-id="17059-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="17059-116">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="17059-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-117">Olay tabanlı zaman uyumsuz model uygulayan bir bileşenin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="17059-118">Bu, bileşenin herhangi bir uygulama modelinde doğru şekilde çalıştığından emin olmak için <xref:System.ComponentModel?displayProperty=nameWithType> ad alanındaki yardımcı sınıflar kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="17059-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="17059-119">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama</span><span class="sxs-lookup"><span data-stu-id="17059-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-120">Olay tabanlı zaman uyumsuz model uygulayan bir bileşeni kullanan bir istemcinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="17059-121">Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="17059-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="17059-122">Olay tabanlı zaman uyumsuz stili destekleyen bir bileşenin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="17059-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="17059-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="17059-124"><xref:System.ComponentModel.AsyncOperation> sınıfını açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="17059-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="17059-125"><xref:System.ComponentModel.AsyncOperationManager> sınıfını açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="17059-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="17059-126"><xref:System.ComponentModel.BackgroundWorker> bileşeni tanımlar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="17059-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17059-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="17059-127">Related Sections</span></span>

 [<span data-ttu-id="17059-128">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="17059-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="17059-129">Zaman uyumsuz ve paralel işlemler için bir programlama modeli tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17059-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="17059-130">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="17059-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="17059-131">.NET 'teki çoklu iş parçacığı özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="17059-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17059-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17059-132">See also</span></span>

- [<span data-ttu-id="17059-133">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="17059-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="17059-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="17059-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="17059-135">Zaman uyumsuz programlama tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="17059-135">Asynchronous Programming Design Patterns</span></span>](index.md)
