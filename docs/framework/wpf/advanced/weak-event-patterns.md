---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991797"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="cd309-102">Zayıf Olay Desenleri</span><span class="sxs-lookup"><span data-stu-id="cd309-102">Weak Event Patterns</span></span>
<span data-ttu-id="cd309-103">Uygulamalarda, olay kaynaklarına eklenmiş olan işleyiciler, işleyiciyi kaynağa bağlayan dinleyici nesnesiyle birlikte yok edilmez.</span><span class="sxs-lookup"><span data-stu-id="cd309-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="cd309-104">Bu durum bellek sızıntılarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd309-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="cd309-105">, belirli olaylar için adanmış bir yönetici sınıfı sağlayarak ve bu olay için dinleyicilerine bir arabirim uygulayarak bu sorunu gidermek için kullanılabilecek bir tasarım kalıbı sunar.</span><span class="sxs-lookup"><span data-stu-id="cd309-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="cd309-106">Bu tasarım deseninin *zayıf olay deseninin*olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd309-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="cd309-107">Neden zayıf olay deseninin uygulanması?</span><span class="sxs-lookup"><span data-stu-id="cd309-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="cd309-108">Olayları dinlemek bellek sızıntılarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd309-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="cd309-109">Bir olayı dinlemek için tipik bir yöntem, bir kaynak üzerindeki olaya bir işleyici ekleyen dile özgü söz dizimini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="cd309-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="cd309-110">Örneğin, ' de C#, söz dizimi: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="cd309-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="cd309-111">Bu teknik, olay kaynağından olay dinleyicisine güçlü bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd309-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="cd309-112">Genellikle, bir dinleyici için bir olay işleyicisi iliştirmek, dinleyicinin, kaynağın nesne ömrü tarafından etkilenen bir nesne yaşam süresine sahip olmasına neden olur (olay işleyicisi açıkça kaldırılmadığı takdirde).</span><span class="sxs-lookup"><span data-stu-id="cd309-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="cd309-113">Ancak belirli durumlarda, dinleyicinin nesne yaşam süresinin, uygulamanın yaşam süresine göre değil, uygulamanın görsel ağacına ait olup olmadığı gibi diğer faktörlere göre denetlenmesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd309-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="cd309-114">Kaynak nesne ömrü, dinleyicinin nesne ömrünü aşacak şekilde genişlediğinde, normal olay deseninin bir bellek sızıntısına yol açar: dinleyici, amaçlarından daha uzun bir süre etkin tutulur.</span><span class="sxs-lookup"><span data-stu-id="cd309-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="cd309-115">Zayıf olay deseninin bu bellek sızıntısı sorununu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd309-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="cd309-116">Zayıf olay alanı, bir dinleyicinin bir olaya kaydolması gerektiğinde kullanılabilir, ancak dinleyici ne zaman kaydı kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="cd309-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="cd309-117">Zayıf olay deseninin, kaynağın nesne ömrü, dinleyicinin yararlı nesne ömrünü aştığında de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd309-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="cd309-118">(Bu durumda, *yararlı* olarak sizin tarafınızdan belirlenir.) Zayıf olay deseninin, dinleyicinin herhangi bir şekilde nesne ömrü özelliklerini etkilemeden olay için kaydolmasına ve bu olayı almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd309-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="cd309-119">Aslında, kaynaktan kapsanan başvuru, dinleyicinin çöp toplama için uygun olup olmadığını belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="cd309-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="cd309-120">Başvuru zayıf bir başvurudur, bu nedenle zayıf olay deseninin ve ilgili API 'lerin adlandırılması.</span><span class="sxs-lookup"><span data-stu-id="cd309-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="cd309-121">Dinleyici atık olarak toplanamaz veya başka bir şekilde yok edilebilir ve kaynak olmayan işleyici başvurularını artık yok edilmiş bir nesneye korumadan devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="cd309-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="cd309-122">Zayıf olay deseninin kim tarafından uygulanması gerekir?</span><span class="sxs-lookup"><span data-stu-id="cd309-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="cd309-123">Zayıf olay deseninin uygulanması, birincil olarak denetim yazarları için ilginç bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="cd309-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="cd309-124">Denetim yazarı olarak, denetiminizin davranışından ve kapsamasından büyük ölçüde sorumlu olursunuz ve onun eklendiği uygulamalarla ilgili etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="cd309-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="cd309-125">Bu, özellikle açıklanan bellek sızıntısı sorununu işlemede denetim nesnesi ömrü davranışını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd309-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="cd309-126">Belirli senaryolar doğal olarak zayıf olay deseninin uygulamasına ödünç vermez.</span><span class="sxs-lookup"><span data-stu-id="cd309-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="cd309-127">Bu tür bir senaryo, veri bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="cd309-127">One such scenario is data binding.</span></span> <span data-ttu-id="cd309-128">Veri bağlamada, kaynak nesnenin bağlama hedefi olan dinleyici nesnesinden tamamen bağımsız olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="cd309-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="cd309-129">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Veri bağlamasının birçok yönü, olayların nasıl uygulandığı konusunda zayıf olay deseninin zaten uygulanmış olması.</span><span class="sxs-lookup"><span data-stu-id="cd309-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="cd309-130">Zayıf olay deseninin nasıl uygulanacağı</span><span class="sxs-lookup"><span data-stu-id="cd309-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="cd309-131">Zayıf olay deseninin uygulanması için üç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="cd309-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="cd309-132">Aşağıdaki tabloda üç yaklaşım listelenmekte ve her birini ne zaman kullanmanız gerektiği hakkında bazı rehberlik sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd309-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="cd309-133">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="cd309-133">Approach</span></span>|<span data-ttu-id="cd309-134">Ne zaman uygulanacağı</span><span class="sxs-lookup"><span data-stu-id="cd309-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="cd309-135">Varolan zayıf bir olay Yöneticisi sınıfını kullan</span><span class="sxs-lookup"><span data-stu-id="cd309-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="cd309-136">Abone olmak istediğiniz olaya karşılık gelen <xref:System.Windows.WeakEventManager>varsa, var olan zayıf olay yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd309-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="cd309-137">WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için, <xref:System.Windows.WeakEventManager> sınıfındaki devralma hiyerarşisine bakın.</span><span class="sxs-lookup"><span data-stu-id="cd309-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="cd309-138">Dahil edilen zayıf olay yöneticileri sınırlı olduğundan, muhtemelen diğer yaklaşımlardan birini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd309-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="cd309-139">Genel bir zayıf olay Yöneticisi sınıfı kullanın</span><span class="sxs-lookup"><span data-stu-id="cd309-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="cd309-140"><xref:System.Windows.WeakEventManager%602> Mevcut<xref:System.Windows.WeakEventManager> olmadığında genel ' i kullanın, uygulanması kolay bir yol istersiniz ve verimlilik konusunda endişe etmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cd309-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="cd309-141">Genel <xref:System.Windows.WeakEventManager%602> , mevcut veya özel zayıf bir olay yöneticisinden daha az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="cd309-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="cd309-142">Örneğin, genel sınıf, olayın adı verilen olayı bulmaya yönelik daha fazla yansıma yapar.</span><span class="sxs-lookup"><span data-stu-id="cd309-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="cd309-143">Ayrıca, genel <xref:System.Windows.WeakEventManager%602> kullanılarak olayı kaydeden kod, var olan veya özel <xref:System.Windows.WeakEventManager>kullanmaktan daha ayrıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="cd309-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="cd309-144">Özel bir zayıf olay Yöneticisi sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd309-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="cd309-145"><xref:System.Windows.WeakEventManager> Mevcut<xref:System.Windows.WeakEventManager> olmadığında ve en iyi verimliliği istediğinizde bir özel oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd309-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="cd309-146">Bir olaya abone <xref:System.Windows.WeakEventManager> olmak için özel kullanmak daha verimli olacaktır, ancak başlangıçta daha fazla kod yazma maliyetine tabi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="cd309-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="cd309-147">Üçüncü taraf zayıf bir olay Yöneticisi kullanma</span><span class="sxs-lookup"><span data-stu-id="cd309-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="cd309-148">NuGet [birkaç zayıf olay yöneticilerine](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) sahiptir ve birçok WPF çerçevesi de (örneğin, [esnek olarak bağlanmış olay aboneliği ile ilgili belgelere](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)bakın).</span><span class="sxs-lookup"><span data-stu-id="cd309-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="cd309-149">Aşağıdaki bölümlerde, zayıf olay deseninin nasıl uygulanacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cd309-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="cd309-150">Bu tartışmanın amaçları doğrultusunda Abone olunacak olay aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd309-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="cd309-151">Olay adı `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="cd309-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="cd309-152">Olay, `EventSource` sınıfı tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cd309-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="cd309-153">Olay işleyicisinin türü: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="cd309-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="cd309-154">Olay, olay işleyicilere türünde `SomeEventEventArgs` bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="cd309-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="cd309-155">Var olan zayıf bir olay Yöneticisi sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="cd309-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd309-156">Var olan zayıf bir olay Yöneticisi bulun.</span><span class="sxs-lookup"><span data-stu-id="cd309-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="cd309-157">WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için, <xref:System.Windows.WeakEventManager> sınıfındaki devralma hiyerarşisine bakın.</span><span class="sxs-lookup"><span data-stu-id="cd309-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="cd309-158">Normal olay kancası yerine yeni zayıf olay yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd309-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd309-159">Örneğin, kodunuz bir olaya abone olmak için aşağıdaki kalıbı kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd309-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd309-160">Aşağıdaki düzene göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd309-160">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd309-161">Benzer şekilde, kodunuz bir olaydan aboneliği kaldırmak için aşağıdaki kalıbı kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd309-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd309-162">Aşağıdaki düzene göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd309-162">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="cd309-163">Genel zayıf olay Yöneticisi sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="cd309-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd309-164">Normal olay kancası <xref:System.Windows.WeakEventManager%602> yerine genel sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd309-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd309-165">Olay dinleyicilerini <xref:System.Windows.WeakEventManager%602> kaydetmek için kullandığınızda, aşağıdaki kodda gösterildiği gibi, olay kaynağını <xref:System.EventArgs> ve türü sınıf için tür parametreleri olarak girin ve çağırın <xref:System.Windows.WeakEventManager%602.AddHandler%2A> :</span><span class="sxs-lookup"><span data-stu-id="cd309-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="cd309-166">Özel bir zayıf olay Yöneticisi sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd309-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd309-167">Aşağıdaki sınıf şablonunu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cd309-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="cd309-168">Bu sınıf <xref:System.Windows.WeakEventManager> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="cd309-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="cd309-169">`SomeEventWeakEventManager` Adı kendi adınızla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd309-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="cd309-170">Daha önce açıklanan üç adı, olaylarınızın karşılık gelen adlarıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd309-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="cd309-171">(`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="cd309-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="cd309-172">Zayıf olay Yöneticisi sınıfının görünürlüğünü (ortak/iç/özel), yönettiği olayla aynı görünürlüğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd309-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="cd309-173">Normal olay kancası yerine yeni zayıf olay yöneticisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd309-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd309-174">Örneğin, kodunuz bir olaya abone olmak için aşağıdaki kalıbı kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd309-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd309-175">Aşağıdaki düzene göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd309-175">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd309-176">Benzer şekilde, kodunuz bir olaya abonelik kaldırmak için aşağıdaki kalıbı kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd309-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="cd309-177">Aşağıdaki düzene göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd309-177">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cd309-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd309-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="cd309-179">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd309-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="cd309-180">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd309-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
