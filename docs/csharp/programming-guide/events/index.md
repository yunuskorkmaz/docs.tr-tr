---
title: "Olaylar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ab40de46bf198cf683ec4847a42d88b3d4807e0
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="a55bf-102">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a55bf-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="a55bf-103">Olayları etkinleştir bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya diğer bildirmek için nesne sınıfları nesneleri çeken bir şey olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a55bf-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="a55bf-104">Gönderir sınıfı (veya *başlatır*) olay çağrılır *yayımcı* ve alma sınıfları (veya *işlemek*) olay çağrılır *aboneleri* .</span><span class="sxs-lookup"><span data-stu-id="a55bf-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="a55bf-105">Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olun.</span><span class="sxs-lookup"><span data-stu-id="a55bf-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="a55bf-106">Kullanabileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] tümleşik geliştirme ortamı (IDE) bir denetim yayımlar etkinliklere göz atın ve işlemek için istediğiniz olanları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a55bf-106">You can use the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="a55bf-107">IDE boş olay işleyicisi yöntemi ve olaya abone için kodu otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="a55bf-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="a55bf-108">Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="a55bf-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="a55bf-109">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a55bf-109">Events Overview</span></span>  
 <span data-ttu-id="a55bf-110">Olayları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a55bf-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="a55bf-111">Yayımcı, ne zaman bir olay tetiklenir belirler; aboneleri olaya yanıt olarak yapılan eylemi belirler.</span><span class="sxs-lookup"><span data-stu-id="a55bf-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="a55bf-112">Bir olay birden çok abone olabilir.</span><span class="sxs-lookup"><span data-stu-id="a55bf-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="a55bf-113">Bir abonenin birden çok yayımcılar birden çok olaylarından işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a55bf-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="a55bf-114">Abone olan olayları hiçbir zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a55bf-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="a55bf-115">Olaylar, genellikle kullanıcı eylemlerini düğme tıklamaları veya menü seçimleri grafik kullanıcı arabirimleri gibi göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a55bf-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="a55bf-116">Bir olay birden çok abone olduğunda, bir olay oluşturulduğunda olay işleyicileri zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a55bf-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="a55bf-117">Olaylar zaman uyumsuz olarak çağırmak için bkz: [çağırma zaman uyumlu yöntemleri zaman uyumsuz olarak](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="a55bf-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="a55bf-118">İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı olayları temel <xref:System.EventHandler> temsilci ve <xref:System.EventArgs> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a55bf-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a55bf-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a55bf-119">Related Sections</span></span>  
 <span data-ttu-id="a55bf-120">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="a55bf-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a55bf-121">Nasıl yapılır: abone olaylara ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="a55bf-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="a55bf-122">Nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="a55bf-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="a55bf-123">Nasıl yapılır: türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="a55bf-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="a55bf-124">Nasıl yapılır: arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="a55bf-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="a55bf-125">İş parçacığı eşitleme</span><span class="sxs-lookup"><span data-stu-id="a55bf-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="a55bf-126">Nasıl yapılır: olay örneklerini depolamak için Sözlük kullanma</span><span class="sxs-lookup"><span data-stu-id="a55bf-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="a55bf-127">Nasıl yapılır: özel olay erişimcilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="a55bf-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a55bf-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a55bf-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="a55bf-129">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="a55bf-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="a55bf-130">[Temsilciler ve olaylar Lambda ifadeleri](http://go.microsoft.com/fwlink/?LinkId=195395) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="a55bf-130">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="a55bf-131">[Temsilciler ve olaylar](http://go.microsoft.com/fwlink/?LinkId=195418) içinde [öğrenme C# 3.0: C# 3.0 ile ilgili temel bilgileri Yöneticisi](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="a55bf-131">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55bf-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a55bf-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="a55bf-133">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a55bf-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a55bf-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a55bf-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="a55bf-135">Windows Forms'ta olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a55bf-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="a55bf-136">Olay tabanlı zaman uyumsuz desen ile birden çok iş parçacıklı programlama</span><span class="sxs-lookup"><span data-stu-id="a55bf-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
