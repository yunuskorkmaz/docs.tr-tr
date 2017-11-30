---
title: "Olay tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8dcd1003b3f93db733ece4f90340d1d98867d2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-design"></a><span data-ttu-id="4093a-102">Olay tasarım</span><span class="sxs-lookup"><span data-stu-id="4093a-102">Event Design</span></span>
<span data-ttu-id="4093a-103">Olayları geri aramalar (Framework'te kullanıcı kodu içine çağırmak izin yapıları) en yaygın kullanılan biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4093a-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="4093a-104">Diğer geri çağırma düzenekler Temsilciler, sanal üyeleri ve arabirim tabanlı eklentiler alma üyeleri içerir. Kullanılabilirlik incelemeleri verilerden geliştiriciler çoğunluğu için bir geri çağırma mekanizmaları kullanan çok olayları kullanarak daha rahat olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4093a-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="4093a-105">Olayları sorunsuz şekilde Visual Studio ve birçok dilde ile tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="4093a-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="4093a-106">Olayların iki grup olduğunu dikkate almak önemlidir: öncesi olaylar ve durum değişiklikler sonra oluşturulan olaylara adlı Sistem değişiklikleri durumunu önce başlatılan olayları sonrası olayları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4093a-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="4093a-107">Bir ön olayının bir örnek olabilir `Form.Closing`, bir form kapatılmadan önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="4093a-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="4093a-108">Bir örnek sonrası olay olabilir `Form.Closed`, bir form kapatıldıktan sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="4093a-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="4093a-109">**✓ YAPMAK** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın</span><span class="sxs-lookup"><span data-stu-id="4093a-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="4093a-110">**✓ YAPMAK** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.</span><span class="sxs-lookup"><span data-stu-id="4093a-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="4093a-111">**✓ DÜŞÜNÜN** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.</span><span class="sxs-lookup"><span data-stu-id="4093a-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="4093a-112">Bir API kullanarak gönderirseniz `EventArgs` doğrudan, hiç olay ile uyumluluk bozmadan gerçekleştirilmesi için herhangi bir veri eklemek kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4093a-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="4093a-113">Bir alt sınıfı kullanırsanız, hatta tamamen başlangıçta boş, gerektiğinde alt özellikleri eklemeniz mümkün olup olmayacağını.</span><span class="sxs-lookup"><span data-stu-id="4093a-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="4093a-114">**✓ YAPMAK** her olay oluşturmak için korumalı sanal bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="4093a-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="4093a-115">Bu durum yalnızca korumasız sınıflar, yapılar, sealed sınıfları veya statik olaylar üzerinde statik olmayan olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4093a-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="4093a-116">Yöntemin amacı bir geçersiz kılma kullanılarak olayını işlemek türetilmiş bir sınıf için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4093a-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="4093a-117">Geçersiz kılma türetilmiş sınıflarda temel sınıf olayları işlemek için daha esnek, daha hızlı ve daha doğal bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="4093a-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="4093a-118">Kural tarafından yöntemin adını "ile" başlatmak ve olayın adı izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="4093a-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="4093a-119">Türetilmiş sınıf kendi geçersiz kılmada yönteminin temel uygulamayı çağırması değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4093a-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="4093a-120">Bunun için herhangi bir işlem düzgün çalışması için temel sınıf gereklidir yöntemi ekleyerek değil hazır olun.</span><span class="sxs-lookup"><span data-stu-id="4093a-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="4093a-121">**✓ YAPMAK** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="4093a-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="4093a-122">Parametre adlı `e` ve olay bağımsız değişkeni sınıf olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4093a-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="4093a-123">**X yok** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="4093a-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="4093a-124">**✓ YAPMAK** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="4093a-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="4093a-125">**X yok** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.</span><span class="sxs-lookup"><span data-stu-id="4093a-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="4093a-126">Geçmesi `EventArgs.Empty` olay yöntemi işleme için herhangi bir veri geçirmek istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4093a-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="4093a-127">Geliştiriciler null olmaması için bu parametreyi bekler.</span><span class="sxs-lookup"><span data-stu-id="4093a-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="4093a-128">**✓ DÜŞÜNÜN** son kullanıcı iptal edebilirsiniz olaylar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4093a-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="4093a-129">Bu, yalnızca ön olayları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4093a-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="4093a-130">Kullanım <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya onun bir alt olayları iptal etmek son kullanıcı izin vermek için olay bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="4093a-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="4093a-131">Özel olay işleyicisi tasarım</span><span class="sxs-lookup"><span data-stu-id="4093a-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="4093a-132">Hangi durumlarda vardır `EventHandler<T>` Framework'te genel türler desteklememektedir CLR önceki sürümleri ile çalışması gerektiği zaman gibi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4093a-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="4093a-133">Böyle durumlarda, özel olay işleyici temsilcisi tasarlayıp gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4093a-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="4093a-134">**✓ YAPMAK** dönüş türü void olay işleyicileri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4093a-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="4093a-135">Olay işleyici birden çok olay işleme yöntemleri, büyük olasılıkla birden fazla nesne çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4093a-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="4093a-136">Olay işleme yöntemleri bir değer döndürmesi izin verilmekteydi her olay başlatma için birden çok dönüş değerlerini olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4093a-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="4093a-137">**✓ YAPMAK** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.</span><span class="sxs-lookup"><span data-stu-id="4093a-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="4093a-138">**✓ YAPMAK** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.</span><span class="sxs-lookup"><span data-stu-id="4093a-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="4093a-139">**X yok** olay işleyicileri ikiden fazla parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="4093a-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="4093a-140">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="4093a-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4093a-141">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="4093a-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4093a-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4093a-142">See Also</span></span>  
 [<span data-ttu-id="4093a-143">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4093a-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="4093a-144">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4093a-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
