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
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741679"
---
# <a name="event-design"></a><span data-ttu-id="2a1b9-102">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="2a1b9-102">Event Design</span></span>
<span data-ttu-id="2a1b9-103">Olaylar en yaygın olarak kullanılan geri çağırma biçimidir (Framework 'ün Kullanıcı koduna çağrı yapmasına izin veren yapılar).</span><span class="sxs-lookup"><span data-stu-id="2a1b9-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="2a1b9-104">Diğer geri çağırma mekanizmaları, temsilciler, sanal üyeler ve arabirim tabanlı eklentiler alan üyeleri içerir. kullanılabilirlik çalışmalarından veriler, geliştiricilerin büyük bir bölümünün diğer geri çağırma mekanizmalarını kullandıklarından daha rahat olduğunu belirtir .</span><span class="sxs-lookup"><span data-stu-id="2a1b9-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="2a1b9-105">Olaylar, Visual Studio ve birçok dil ile tamamen tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="2a1b9-106">İki olay grubu olduğunu unutmamak önemlidir: bir sistem değişikliği durumu, ön olaylar adı ve durum değişikliklerinden sonra oluşturulan olaylar, olaylar sonrası olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="2a1b9-107">Bir form kapatılmadan önce oluşturulan `Form.Closing`ön olaya bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="2a1b9-108">Bir form kapatıldıktan sonra oluşturulan olay sonrası `Form.Closed`bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="2a1b9-109">✔️ "yangın" veya "tetikleyici" yerine olaylar için "Raise" terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="2a1b9-110">✔️ olay işleyicileri olarak kullanılacak yeni temsilciler el ile oluşturmak yerine <xref:System.EventHandler%601?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="2a1b9-111">✔️, olayın olay işleme yöntemine hiçbir şekilde herhangi bir veri taşıması gerekmeyeceğinden kesinlikle emin olmadığınız sürece, olay bağımsız değişkeni olarak <xref:System.EventArgs> bir alt sınıfını kullanmayı düşünün. Bu durumda, `EventArgs` türünü doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="2a1b9-112">Doğrudan `EventArgs` kullanarak bir API dağıtırsanız, hiçbir veri, hiçbir şekilde, hiçbir verileri hiçbir şekilde uyumluluk olmadan bu olayla birlikte ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="2a1b9-113">Bir alt sınıf kullanırsanız, başlangıçta tamamen boş olsalar bile, gerektiğinde alt sınıfa özellikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="2a1b9-114">✔️ her olayı yükseltmek için korumalı bir sanal yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="2a1b9-115">Bu yalnızca korumasız sınıflarda, yapıları, mühürlü sınıfları veya statik olayları değil, statik olmayan olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="2a1b9-116">Yönteminin amacı, bir geçersiz kılma kullanarak bir türetilmiş sınıfın olayı işlemesi için bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="2a1b9-117">Geçersiz kılma türetilmiş sınıflarda temel sınıf olaylarını işlemek için daha esnek, daha hızlı ve daha doğal bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="2a1b9-118">Kurala göre, yöntemin adı "on" ile başlamalı ve bunun ardından olayın adı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="2a1b9-119">Türetilmiş sınıf, geçersiz kılma içindeki yöntemin temel uygulamasını çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="2a1b9-120">Temel sınıfın düzgün çalışması için gerekli olan yöntemde herhangi bir işlem dahil edilmez, bunun için hazırlıklı olun.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="2a1b9-121">✔️, bir olayı başlatan korumalı yönteme tek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="2a1b9-122">Parametresi `e` olarak adlandırılmalıdır ve olay bağımsız değişkeni sınıfı olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="2a1b9-123">statik olmayan bir olay oluşturulurken ❌ gönderen olarak null geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="2a1b9-124">statik bir olay oluştururken ✔️ gönderen olarak null geçirin.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="2a1b9-125">❌ bir olayı oluştururken olay verileri parametresi olarak null geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="2a1b9-126">Herhangi bir veriyi olay işleme yöntemine geçirmek istemiyorsanız `EventArgs.Empty` geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="2a1b9-127">Geliştiriciler bu parametrenin null olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="2a1b9-128">✔️ Son kullanıcının iptal edebilmesini sağlayan olayları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="2a1b9-129">Bu yalnızca ön olaylar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="2a1b9-130">Son kullanıcının olayları iptal edebilmesini sağlamak için olay bağımsız değişkeni olarak <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya alt sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="2a1b9-131">Özel olay Işleyicisi tasarımı</span><span class="sxs-lookup"><span data-stu-id="2a1b9-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="2a1b9-132">Framework 'ün, genel türleri desteklemeyen CLR 'nin önceki sürümleriyle çalışması gerektiği durumlar gibi `EventHandler<T>` kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="2a1b9-133">Bu gibi durumlarda, özel bir olay işleyicisi temsilcisi tasarlamanızı ve geliştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="2a1b9-134">✔️ olay işleyicileri için void dönüş türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="2a1b9-135">Bir olay işleyicisi, muhtemelen birden çok nesnede çok sayıda olay işleme yöntemini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="2a1b9-136">Olay işleme yöntemlerinin bir değer döndürmesine izin veriliyorsa, her olay çağrısı için birden fazla dönüş değeri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="2a1b9-137">✔️ olay işleyicisinin ilk parametresinin türü olarak `object` kullanın ve `sender`çağırır.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="2a1b9-138">✔️ <xref:System.EventArgs?displayProperty=nameWithType> veya alt sınıfını olay işleyicisinin ikinci parametresinin türü olarak kullanın ve `e`çağırın.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="2a1b9-139">❌ olay işleyicilerinde ikiden fazla parametre yok.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="2a1b9-140">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2a1b9-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2a1b9-141">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="2a1b9-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2a1b9-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-142">See also</span></span>

- [<span data-ttu-id="2a1b9-143">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2a1b9-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="2a1b9-144">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2a1b9-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
