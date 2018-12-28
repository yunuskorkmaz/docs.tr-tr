---
title: Olaylar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 55fe0e8f94d9b350305b634cabb90011e173b572
ms.sourcegitcommit: 882a2f56bf6afdcb40d468e4ae9371296822b68c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2018
ms.locfileid: "53451150"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="7bbc0-102">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7bbc0-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="7bbc0-103">Olayları etkinleştirmektedir bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya diğer bildirmek için nesne sınıfları veya nesneleri ilgilendiğiniz bir sorun oluştuğunda.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="7bbc0-104">Gönderen sınıfı (veya *başlatır*) olay çağrılır *yayımcı* ve alan sınıfları (veya *işlemek*) olay çağrılır *aboneleri* .</span><span class="sxs-lookup"><span data-stu-id="7bbc0-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="7bbc0-105">Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimleri tarafından oluşturulan olaylara abone olun.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="7bbc0-106">Visual C# tümleşik geliştirme ortamı (IDE) bir denetim yayımlayan olayları ve kullanmak istediğiniz olanları seçmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="7bbc0-107">IDE boş olay işleyicisi yöntemi ve olaya abone olmak için kodu otomatik olarak eklemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="7bbc0-108">Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="7bbc0-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="7bbc0-109">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7bbc0-109">Events Overview</span></span>  
 <span data-ttu-id="7bbc0-110">Olayları, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7bbc0-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="7bbc0-111">Yayımcı, bir olay olduğunda tetiklenir belirler; Aboneler, olaya yanıt olarak yapılan bir eylemi belirler.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="7bbc0-112">Bir olayın birden fazla aboneye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="7bbc0-113">Bir abonenin birden çok yayımcılardan birden çok olay işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="7bbc0-114">Abone olan olaylar hiçbir zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="7bbc0-115">Olaylar genellikle, düğme tıklamaları veya grafik kullanıcı arabirimleri menü seçimleri gibi kullanıcı eylemlerini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="7bbc0-116">Bir olay birden çok abone olduğunda, bir olay oluştuğunda olay işleyicileri zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="7bbc0-117">Olayları zaman uyumsuz olarak çağırma hakkında bilgi için bkz: [uyumsuz zaman uyumlu yöntemleri çağırma](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="7bbc0-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="7bbc0-118">İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı, olayları temel <xref:System.EventHandler> temsilci ve <xref:System.EventArgs> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7bbc0-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7bbc0-119">Related Sections</span></span>  
 <span data-ttu-id="7bbc0-120">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="7bbc0-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="7bbc0-121">Nasıl yapılır: Abone olaylara ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="7bbc0-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="7bbc0-122">Nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="7bbc0-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="7bbc0-123">Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları Yükselt</span><span class="sxs-lookup"><span data-stu-id="7bbc0-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="7bbc0-124">Nasıl yapılır:  Arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="7bbc0-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="7bbc0-125">Nasıl yapılır: Store olay örnekleri için Sözlük kullanma</span><span class="sxs-lookup"><span data-stu-id="7bbc0-125">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="7bbc0-126">Nasıl yapılır: Özel olay erişimcilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="7bbc0-126">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="7bbc0-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7bbc0-127">C# Language Specification</span></span>  

<span data-ttu-id="7bbc0-128">Daha fazla bilgi için [olayları](~/_csharplang/spec/classes.md#events) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bbc0-128">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="7bbc0-129">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-129">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="7bbc0-130">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="7bbc0-130">Featured Book Chapters</span></span>  
 <span data-ttu-id="7bbc0-131">[Temsilciler, olayları ve Lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) içinde [ C# 3.0 Cookbook, Third Edition: İçin 250'den fazla çözüm C# 3.0 programcıları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="7bbc0-131">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="7bbc0-132">[Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) içinde [öğrenme C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="7bbc0-132">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bbc0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bbc0-133">See Also</span></span>

- <xref:System.EventHandler>  
- [<span data-ttu-id="7bbc0-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7bbc0-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7bbc0-135">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="7bbc0-135">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="7bbc0-136">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7bbc0-136">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
