---
title: Olaylar-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: e15c3d124b4d1c30e2f9bb9f44b40e25b6a72346
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240733"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="19f59-102">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="19f59-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="19f59-103">Olaylar, bir [sınıf](../../language-reference/keywords/class.md) ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19f59-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="19f59-104">Olayı gönderen (veya *başlatan*) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya *işleyen*) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="19f59-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="19f59-105">Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olursunuz.</span><span class="sxs-lookup"><span data-stu-id="19f59-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="19f59-106">Visual C# tümleşik geliştirme ortamı 'nı (IDE) bir denetimin yayımladığı olaylara gözatıp işlemek istediğiniz olanları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19f59-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="19f59-107">IDE, otomatik olarak boş bir olay işleyici yöntemi ve olaya abone olmak için kod eklemenin kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="19f59-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="19f59-108">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="19f59-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="19f59-109">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="19f59-109">Events Overview</span></span>  
 <span data-ttu-id="19f59-110">Olaylar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="19f59-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="19f59-111">Yayımcı bir olayın ne zaman gerçekleştiğini belirler; aboneler olaya yanıt olarak hangi eylemin alınacağını tespit ediyor.</span><span class="sxs-lookup"><span data-stu-id="19f59-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="19f59-112">Bir olay birden çok aboneye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="19f59-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="19f59-113">Bir abone birden çok yayımcıların birden çok olayını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="19f59-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="19f59-114">Abone olmayan olaylar hiçbir şekilde oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="19f59-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="19f59-115">Olaylar genellikle grafik kullanıcı arabirimlerinde düğme tıklamaları veya menü seçimleri gibi kullanıcı eylemlerini işaret etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19f59-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="19f59-116">Bir olayda birden çok abone olduğunda, olay işleyicileri bir olay oluşturulduğunda zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19f59-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="19f59-117">Olayları zaman uyumsuz olarak çağırmak için bkz. [zaman uyumlu yöntemleri zaman uyumsuz çağırma](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="19f59-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="19f59-118">.NET Framework sınıf kitaplığında, olaylar <xref:System.EventHandler> temsilciyi ve <xref:System.EventArgs> temel sınıfı temel alır.</span><span class="sxs-lookup"><span data-stu-id="19f59-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="19f59-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="19f59-119">Related Sections</span></span>  
 <span data-ttu-id="19f59-120">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="19f59-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="19f59-121">Olaylara abone olma ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="19f59-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="19f59-122">.NET yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="19f59-122">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="19f59-123">Türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="19f59-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="19f59-124">Arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="19f59-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="19f59-125">Özel olay erişimcilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="19f59-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="19f59-126">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="19f59-126">C# Language Specification</span></span>  

<span data-ttu-id="19f59-127">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Olaylar](~/_csharplang/spec/classes.md#events) .</span><span class="sxs-lookup"><span data-stu-id="19f59-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="19f59-128">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="19f59-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="19f59-129">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="19f59-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="19f59-130">C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [: c# 3,0 programcıları için 250 ' den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="19f59-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="19f59-131">Öğreniminde [Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) [c# 3,0: C# 3,0 temelleri ana](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="19f59-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f59-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19f59-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="19f59-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="19f59-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="19f59-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="19f59-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="19f59-135">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="19f59-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
