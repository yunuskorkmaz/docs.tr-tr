---
title: Olaylar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 5b844b20ac62b4cbc2a73931eecab95f22b4b1de
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199449"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="004a6-102">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="004a6-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="004a6-103">Olayları etkinleştirmektedir bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya diğer bildirmek için nesne sınıfları veya nesneleri ilgilendiğiniz bir sorun oluştuğunda.</span><span class="sxs-lookup"><span data-stu-id="004a6-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="004a6-104">Gönderen sınıfı (veya *başlatır*) olay çağrılır *yayımcı* ve alan sınıfları (veya *işlemek*) olay çağrılır *aboneleri* .</span><span class="sxs-lookup"><span data-stu-id="004a6-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="004a6-105">Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimleri tarafından oluşturulan olaylara abone olun.</span><span class="sxs-lookup"><span data-stu-id="004a6-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="004a6-106">Visual C# tümleşik geliştirme ortamı (IDE) bir denetim yayımlayan olayları ve kullanmak istediğiniz olanları seçmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="004a6-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="004a6-107">IDE boş olay işleyicisi yöntemi ve olaya abone olmak için kodu otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="004a6-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="004a6-108">Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="004a6-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="004a6-109">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="004a6-109">Events Overview</span></span>  
 <span data-ttu-id="004a6-110">Olayları, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="004a6-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="004a6-111">Yayımcı, bir olay olduğunda tetiklenir belirler; Aboneler, olaya yanıt olarak yapılan bir eylemi belirler.</span><span class="sxs-lookup"><span data-stu-id="004a6-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="004a6-112">Bir olayın birden fazla aboneye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="004a6-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="004a6-113">Bir abonenin birden çok yayımcılardan birden çok olay işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="004a6-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="004a6-114">Abone olan olaylar hiçbir zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="004a6-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="004a6-115">Olaylar genellikle, düğme tıklamaları veya grafik kullanıcı arabirimleri menü seçimleri gibi kullanıcı eylemlerini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="004a6-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="004a6-116">Bir olay birden çok abone olduğunda, bir olay oluştuğunda olay işleyicileri zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="004a6-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="004a6-117">Olayları zaman uyumsuz olarak çağırma hakkında bilgi için bkz: [uyumsuz zaman uyumlu yöntemleri çağırma](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="004a6-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="004a6-118">İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı, olayları temel <xref:System.EventHandler> temsilci ve <xref:System.EventArgs> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="004a6-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="004a6-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="004a6-119">Related Sections</span></span>  
 <span data-ttu-id="004a6-120">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="004a6-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="004a6-121">Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma</span><span class="sxs-lookup"><span data-stu-id="004a6-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="004a6-122">Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama</span><span class="sxs-lookup"><span data-stu-id="004a6-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="004a6-123">Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="004a6-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="004a6-124">Nasıl yapılır: arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="004a6-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="004a6-125">İş Parçacığı Eşitleme</span><span class="sxs-lookup"><span data-stu-id="004a6-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="004a6-126">Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma</span><span class="sxs-lookup"><span data-stu-id="004a6-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="004a6-127">Nasıl yapılır: Özel Olay Erişimcilerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="004a6-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="004a6-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="004a6-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="004a6-129">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="004a6-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="004a6-130">[Temsilciler, olayları ve Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Cookbook, Third Edition: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="004a6-130">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="004a6-131">[Temsilciler ve olaylar](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) içinde [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="004a6-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="004a6-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="004a6-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="004a6-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="004a6-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="004a6-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="004a6-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="004a6-135">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="004a6-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="004a6-136">Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama</span><span class="sxs-lookup"><span data-stu-id="004a6-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
