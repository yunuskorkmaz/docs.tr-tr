---
title: Etkinlikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712318"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="9ff99-102">Olaylar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9ff99-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="9ff99-103">Olaylar, ilgi çekici bir şey oluştuğunda bir [sınıfın](../../language-reference/keywords/class.md) veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ff99-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="9ff99-104">Olayı gönderen (veya *yükselten)* sınıfa *yayımcı,* olayı alan (veya *işleyen)* sınıflara *abone*denir.</span><span class="sxs-lookup"><span data-stu-id="9ff99-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="9ff99-105">Tipik bir C# Windows Formları veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından yükseltilen olaylara abone olursunuz.</span><span class="sxs-lookup"><span data-stu-id="9ff99-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="9ff99-106">Denetimin yayımettiği olaylara göz atmak ve işlemek istediğiniz etkinlikleri seçmek için Visual C# tümleşik geliştirme ortamını (IDE) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ff99-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="9ff99-107">IDE, boş bir olay işleyicisi yöntemini ve olaya abone olmak için kodu otomatik olarak eklemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ff99-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="9ff99-108">Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](./how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="9ff99-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="9ff99-109">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ff99-109">Events Overview</span></span>  
 <span data-ttu-id="9ff99-110">Olaylar aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9ff99-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="9ff99-111">Yayımcı, bir olayın ne zaman büyütülür olduğunu belirler; aboneler, olaya yanıt olarak hangi eylemin ne olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="9ff99-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="9ff99-112">Bir olayın birden çok abonesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ff99-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="9ff99-113">Abone, birden çok yayımcıdan birden çok olayı işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9ff99-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="9ff99-114">Abonesi olmayan etkinlikler hiçbir zaman yükseltilmez.</span><span class="sxs-lookup"><span data-stu-id="9ff99-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="9ff99-115">Olaylar genellikle düğme tıklamaları veya grafik kullanıcı arabirimlerindeki menü seçimleri gibi kullanıcı eylemlerini işaret lemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ff99-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="9ff99-116">Bir olayın birden çok abonesi olduğunda, bir olay yükseltildiğinde olay işleyicileri eşzamanlı olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9ff99-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="9ff99-117">Olayları eşzamanlı olarak çağırmak için Eşzamanlı [Arama Yöntemlerini Eşitleme'ye](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9ff99-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="9ff99-118">.NET Framework sınıf kitaplığında olaylar <xref:System.EventHandler> temsilcive <xref:System.EventArgs> taban sınıfa dayanır.</span><span class="sxs-lookup"><span data-stu-id="9ff99-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9ff99-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9ff99-119">Related Sections</span></span>  
 <span data-ttu-id="9ff99-120">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff99-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="9ff99-121">Olaylara abone olma ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="9ff99-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="9ff99-122">.NET Framework Yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="9ff99-122">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="9ff99-123">Türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ff99-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="9ff99-124">Arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="9ff99-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="9ff99-125">Özel olay erişimcilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="9ff99-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="9ff99-126">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9ff99-126">C# Language Specification</span></span>  

<span data-ttu-id="9ff99-127">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Etkinlikler'e](~/_csharplang/spec/classes.md#events) bakın.</span><span class="sxs-lookup"><span data-stu-id="9ff99-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="9ff99-128">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="9ff99-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="9ff99-129">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="9ff99-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="9ff99-130">C# 3.0 Yemek Kitabında [Delegeler, Etkinlikler ve Lambda İfadeleri,](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [Üçüncü Baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="9ff99-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="9ff99-131">[C#](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) 3.0 Öğrenmede Delegeler ve [Etkinlikler: C# 3.0'ın temellerinde ustalaşma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="9ff99-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff99-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff99-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="9ff99-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ff99-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ff99-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="9ff99-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="9ff99-135">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ff99-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
