---
title: Olay Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709432"
---
# <a name="event-design"></a><span data-ttu-id="8a08a-102">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="8a08a-102">Event Design</span></span>
<span data-ttu-id="8a08a-103">Olaylar en yaygın olarak kullanılan geri çağırma biçimidir (Framework 'ün Kullanıcı koduna çağrı yapmasına izin veren yapılar).</span><span class="sxs-lookup"><span data-stu-id="8a08a-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="8a08a-104">Diğer geri çağırma mekanizmaları, temsilciler, sanal üyeler ve arabirim tabanlı eklentiler alan üyeleri içerir. kullanılabilirlik çalışmalarından veriler, geliştiricilerin büyük bir bölümünün diğer geri çağırma mekanizmalarını kullandıklarından daha rahat olduğunu belirtir .</span><span class="sxs-lookup"><span data-stu-id="8a08a-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="8a08a-105">Olaylar, Visual Studio ve birçok dil ile tamamen tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="8a08a-106">İki olay grubu olduğunu unutmamak önemlidir: bir sistem değişikliği durumu, ön olaylar adı ve durum değişikliklerinden sonra oluşturulan olaylar, olaylar sonrası olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="8a08a-107">Bir form kapatılmadan önce oluşturulan `Form.Closing`ön olaya bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="8a08a-108">Bir form kapatıldıktan sonra oluşturulan olay sonrası `Form.Closed`bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="8a08a-109">**✓ DO** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın</span><span class="sxs-lookup"><span data-stu-id="8a08a-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="8a08a-110">**✓ DO** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.</span><span class="sxs-lookup"><span data-stu-id="8a08a-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="8a08a-111">**✓ CONSIDER** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.</span><span class="sxs-lookup"><span data-stu-id="8a08a-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="8a08a-112">Doğrudan `EventArgs` kullanarak bir API dağıtırsanız, hiçbir veri, hiçbir şekilde, hiçbir verileri hiçbir şekilde uyumluluk olmadan bu olayla birlikte ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a08a-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="8a08a-113">Bir alt sınıf kullanırsanız, başlangıçta tamamen boş olsalar bile, gerektiğinde alt sınıfa özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a08a-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="8a08a-114">**✓ DO** her olay oluşturmak için korumalı sanal bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a08a-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="8a08a-115">Bu yalnızca korumasız sınıflarda, yapıları, mühürlü sınıfları veya statik olayları değil, statik olmayan olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="8a08a-116">Yönteminin amacı, bir geçersiz kılma kullanarak bir türetilmiş sınıfın olayı işlemesi için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="8a08a-117">Geçersiz kılma türetilmiş sınıflarda temel sınıf olaylarını işlemek için daha esnek, daha hızlı ve daha doğal bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="8a08a-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="8a08a-118">Kurala göre, yöntemin adı "on" ile başlamalı ve bunun ardından olayın adı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="8a08a-119">Türetilmiş sınıf, geçersiz kılma içindeki yöntemin temel uygulamasını çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="8a08a-120">Temel sınıfın düzgün çalışması için gerekli olan yöntemde herhangi bir işlem dahil edilmez, bunun için hazırlıklı olun.</span><span class="sxs-lookup"><span data-stu-id="8a08a-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="8a08a-121">**✓ DO** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="8a08a-122">Parametresi `e` olarak adlandırılmalıdır ve olay bağımsız değişkeni sınıfı olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="8a08a-123">**X DO NOT** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="8a08a-124">**✓ DO** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="8a08a-125">**X DO NOT** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="8a08a-126">Herhangi bir veriyi olay işleme yöntemine geçirmek istemiyorsanız `EventArgs.Empty` geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="8a08a-127">Geliştiriciler bu parametrenin null olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="8a08a-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="8a08a-128">**✓ CONSIDER** son kullanıcı iptal edebilirsiniz olaylar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8a08a-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="8a08a-129">Bu yalnızca ön olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="8a08a-130">Son kullanıcının olayları iptal edebilmesini sağlamak için olay bağımsız değişkeni olarak <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya alt sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a08a-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="8a08a-131">Özel olay Işleyicisi tasarımı</span><span class="sxs-lookup"><span data-stu-id="8a08a-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="8a08a-132">Framework 'ün, genel türleri desteklemeyen CLR 'nin önceki sürümleriyle çalışması gerektiği durumlar gibi `EventHandler<T>` kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8a08a-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="8a08a-133">Bu gibi durumlarda, özel bir olay işleyicisi temsilcisi tasarlamanızı ve geliştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="8a08a-134">**✓ DO** dönüş türü void olay işleyicileri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a08a-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="8a08a-135">Bir olay işleyicisi, muhtemelen birden çok nesnede çok sayıda olay işleme yöntemini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="8a08a-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="8a08a-136">Olay işleme yöntemlerinin bir değer döndürmesine izin veriliyorsa, her olay çağrısı için birden fazla dönüş değeri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8a08a-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="8a08a-137">**✓ DO** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.</span><span class="sxs-lookup"><span data-stu-id="8a08a-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="8a08a-138">**✓ DO** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.</span><span class="sxs-lookup"><span data-stu-id="8a08a-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="8a08a-139">**X DO NOT** olay işleyicileri ikiden fazla parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="8a08a-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="8a08a-140">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8a08a-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8a08a-141">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="8a08a-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a08a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a08a-142">See also</span></span>

- [<span data-ttu-id="8a08a-143">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8a08a-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="8a08a-144">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8a08a-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
