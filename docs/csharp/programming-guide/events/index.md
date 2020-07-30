---
title: Olaylar-C# Programlama Kılavuzu
description: Olaylar hakkında bilgi edinin. Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 3160d1e381c6cb3af0f017538f9555b3fded9910
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302080"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="294e8-104">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="294e8-104">Events (C# Programming Guide)</span></span>
<span data-ttu-id="294e8-105">Olaylar, bir [sınıf](../../language-reference/keywords/class.md) ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="294e8-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="294e8-106">Olayı gönderen (veya *başlatan*) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya *işleyen*) sınıflar *aboneler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="294e8-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="294e8-107">Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olursunuz.</span><span class="sxs-lookup"><span data-stu-id="294e8-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="294e8-108">Visual C# tümleşik geliştirme ortamı 'nı (IDE) bir denetimin yayımladığı olaylara gözatıp işlemek istediğiniz olanları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294e8-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="294e8-109">IDE, otomatik olarak boş bir olay işleyici yöntemi ve olaya abone olmak için kod eklemenin kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="294e8-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="294e8-110">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="294e8-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="294e8-111">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="294e8-111">Events Overview</span></span>  
 <span data-ttu-id="294e8-112">Olaylar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="294e8-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="294e8-113">Yayımcı bir olayın ne zaman gerçekleştiğini belirler; aboneler olaya yanıt olarak hangi eylemin alınacağını tespit ediyor.</span><span class="sxs-lookup"><span data-stu-id="294e8-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="294e8-114">Bir olay birden çok aboneye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="294e8-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="294e8-115">Bir abone birden çok yayımcıların birden çok olayını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="294e8-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="294e8-116">Abone olmayan olaylar hiçbir şekilde oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="294e8-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="294e8-117">Olaylar genellikle grafik kullanıcı arabirimlerinde düğme tıklamaları veya menü seçimleri gibi kullanıcı eylemlerini işaret etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="294e8-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="294e8-118">Bir olayda birden çok abone olduğunda, olay işleyicileri bir olay oluşturulduğunda zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="294e8-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="294e8-119">Olayları zaman uyumsuz olarak çağırmak için bkz. [zaman uyumlu yöntemleri zaman uyumsuz çağırma](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="294e8-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="294e8-120">.NET Framework sınıf kitaplığında, olaylar <xref:System.EventHandler> temsilciyi ve <xref:System.EventArgs> temel sınıfı temel alır.</span><span class="sxs-lookup"><span data-stu-id="294e8-120">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="294e8-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="294e8-121">Related Sections</span></span>  
 <span data-ttu-id="294e8-122">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="294e8-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="294e8-123">Olaylara abone olma ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="294e8-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="294e8-124">.NET yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="294e8-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="294e8-125">Türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="294e8-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="294e8-126">Arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="294e8-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="294e8-127">Özel olay erişimcilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="294e8-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="294e8-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="294e8-128">C# Language Specification</span></span>  

<span data-ttu-id="294e8-129">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Olaylar](~/_csharplang/spec/classes.md#events) .</span><span class="sxs-lookup"><span data-stu-id="294e8-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="294e8-130">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="294e8-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="294e8-131">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="294e8-131">Featured Book Chapters</span></span>  
 <span data-ttu-id="294e8-132">C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [: c# 3,0 programcıları için 250 ' den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="294e8-132">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="294e8-133">Öğreniminde [Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) [c# 3,0: C# 3,0 temelleri ana](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="294e8-133">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294e8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294e8-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="294e8-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="294e8-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="294e8-136">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="294e8-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="294e8-137">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="294e8-137">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
