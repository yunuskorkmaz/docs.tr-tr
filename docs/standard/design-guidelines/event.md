---
title: Olay tasarımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493050"
---
# <a name="event-design"></a><span data-ttu-id="988de-102">Olay tasarımı</span><span class="sxs-lookup"><span data-stu-id="988de-102">Event Design</span></span>
<span data-ttu-id="988de-103">Olayları en yaygın kullanılan geri çağırmalar (kullanıcı koda çağrı için framework izin yapıları) biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="988de-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="988de-104">Başka bir geri çağırma mekanizmalar Temsilciler, sanal üyeleri ve arabirim tabanlı eklentileri alma üyeleri içerir. Kullanılabilirlik incelemeleri verilerden geliştiricilerin çoğu kullandıkları için bir geri çağırma mekanizmaları çok olayları kullanarak daha iyi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="988de-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="988de-105">Olayları Visual Studio ve birçok dili ile sorunsuz şekilde tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="988de-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="988de-106">İki olay gruplarını olduğuna dikkat edin önemlidir: öncesi olayları ve bir durum olarak değiştirdikten sonra oluşturulan olayları adlı Sistem değişiklikleri durumunu önce harekete geçirilen olayları sonrası olayları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="988de-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="988de-107">Bir ön olayının örnek verilebilir `Form.Closing`, bir form kapatılmadan hemen önce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="988de-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="988de-108">Örnek sonrası olayının `Form.Closed`, bir form kapatıldıktan sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="988de-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="988de-109">**✓ DO** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın</span><span class="sxs-lookup"><span data-stu-id="988de-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="988de-110">**✓ DO** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.</span><span class="sxs-lookup"><span data-stu-id="988de-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="988de-111">**✓ CONSIDER** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.</span><span class="sxs-lookup"><span data-stu-id="988de-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="988de-112">Bir API'yi kullanarak gönderdiğimde `EventArgs` doğrudan, hiç olay ile uyumluluk bozup olmadan gerçekleştirilmesi için herhangi bir veri eklemek mümkün olmayacak.</span><span class="sxs-lookup"><span data-stu-id="988de-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="988de-113">Öğesinin alt sınıfı kullanırsanız, hatta başlangıçta tamamen boş, gerektiğinde alt özellikler eklemeniz mümkün olmayacak durumunda.</span><span class="sxs-lookup"><span data-stu-id="988de-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="988de-114">**✓ DO** her olay oluşturmak için korumalı sanal bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="988de-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="988de-115">Bu durum yalnızca statik olmayan olayları mühürsüz sınıflar, yapılar, sınıfları veya statik olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="988de-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="988de-116">Yöntem amacı, bir geçersiz kılma kullanılarak olayı işlemek bir türetilen sınıf için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="988de-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="988de-117">Geçersiz kılma türetilmiş sınıflarda temel sınıf olayları işlemek için daha esnek, daha hızlı ve daha doğal bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="988de-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="988de-118">Kural olarak, yöntemin adı "ile" başlatmak ve olay adıyla izlenmesi.</span><span class="sxs-lookup"><span data-stu-id="988de-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="988de-119">Türetilmiş sınıf, yöntemin taban uygulamasını kendi geçersiz kılma seçeneğinde çağırmamanız seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="988de-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="988de-120">Bu, herhangi bir işlem düzgün çalışması temel sınıf için gerekli olan yönteminde içermeden tarafından hazır olun.</span><span class="sxs-lookup"><span data-stu-id="988de-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="988de-121">**✓ DO** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="988de-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="988de-122">Parametre adlı `e` ve olay bağımsız değişken sınıf olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="988de-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="988de-123">**X DO NOT** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="988de-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="988de-124">**✓ DO** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="988de-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="988de-125">**X DO NOT** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.</span><span class="sxs-lookup"><span data-stu-id="988de-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="988de-126">Geçirmeniz `EventArgs.Empty` olay yöntemi işleme için herhangi bir veri geçirmek istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="988de-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="988de-127">Geliştiriciler bu parametre null olmaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="988de-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="988de-128">**✓ CONSIDER** son kullanıcı iptal edebilirsiniz olaylar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="988de-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="988de-129">Bu, yalnızca öncesi olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="988de-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="988de-130">Kullanım <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya onun alt olayları iptal etmek son kullanıcı izin vermek için olay bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="988de-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="988de-131">Özel olay işleyicisi tasarım</span><span class="sxs-lookup"><span data-stu-id="988de-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="988de-132">Hangi durumlarda vardır `EventHandler<T>` Framework'te genel türler desteklememektedir CLR'nin önceki sürümleriyle çalışmaya gerektiğinde gibi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="988de-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="988de-133">Böyle durumlarda bir özel olay işleyici temsilcisini tasarlayıp gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="988de-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="988de-134">**✓ DO** dönüş türü void olay işleyicileri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="988de-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="988de-135">Bir olay işleyicisi, birden çok olay işleme, birden çok nesnelerde yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="988de-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="988de-136">Bir değer döndürmek için olay işleme yöntemleri izin verilirse, her olay çağırma için birden çok değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="988de-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="988de-137">**✓ DO** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.</span><span class="sxs-lookup"><span data-stu-id="988de-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="988de-138">**✓ DO** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.</span><span class="sxs-lookup"><span data-stu-id="988de-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="988de-139">**X DO NOT** olay işleyicileri ikiden fazla parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="988de-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="988de-140">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="988de-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="988de-141">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="988de-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988de-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="988de-142">See also</span></span>

- [<span data-ttu-id="988de-143">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="988de-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="988de-144">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="988de-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
