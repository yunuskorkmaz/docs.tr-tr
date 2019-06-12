---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 0c5bae64fbbeddedd905e5df0b5789542e29f2f1
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833925"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="cd992-102">Zayıf Olay Desenleri</span><span class="sxs-lookup"><span data-stu-id="cd992-102">Weak Event Patterns</span></span>
<span data-ttu-id="cd992-103">Uygulamalar, olay kaynaklarına bağlı işleyicileri işleyicinin kaynağına bağlı dinleyici nesne ile koordinasyon halinde edilmeyeceği olduğunu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cd992-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="cd992-104">Bu durum, bellek sızıntılarının neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd992-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="cd992-105">belirli olaylar için adanmış yönetici sınıfı sağlayarak ve bu olayın dinleyicileri üzerinde arabirimi uygulama bu sorunu gidermek için kullanılabilecek bir tasarım desenini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="cd992-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="cd992-106">Bu tasarım deseni olarak bilinen *zayıf olay deseni*.</span><span class="sxs-lookup"><span data-stu-id="cd992-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="cd992-107">Zayıf olay deseni neden uygulansın mı?</span><span class="sxs-lookup"><span data-stu-id="cd992-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="cd992-108">Olayları dinleme bellek sızıntılarının neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd992-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="cd992-109">Bir olayı dinlemek için genel teknik, bir kaynak bir olaya bir işleyici ekler dile özgü sözdizimi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="cd992-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="cd992-110">Örneğin, C#, sözdizimi şöyledir: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="cd992-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="cd992-111">Bu teknik, olay kaynağından olay dinleyicisi için güçlü bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd992-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="cd992-112">Normalde, bir dinleyici için bir olay işleyici ekleme (olay işleyici açıkça kaldırılana sürece), kaynak nesnenin ömrünü tarafından etkileyen bir nesne yaşam süresi dinleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="cd992-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="cd992-113">Ancak bazı durumlarda, şu anda uygulama ve kaynak ömrünü tarafından görsel ağacı ait olup gibi diğer faktörler tarafından denetlenmesi için dinleyici nesne ömrünü isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd992-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="cd992-114">Kaynak nesne ömrü dinleyici nesne yaşam süresi genişletir olduğunda, normal olay deseni bir bellek sızıntısına neden olur: dinleyici istenenden daha uzun süre tutma tutulur.</span><span class="sxs-lookup"><span data-stu-id="cd992-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="cd992-115">Zayıf olay deseni, bu bellek sızıntısı sorunu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd992-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="cd992-116">Zayıf olay deseni bir etkinliğe kaydolmak bir dinleyici gerekiyor, ancak zaman kaydını kaldırmak dinleyici açıkça bilmez olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd992-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="cd992-117">Zayıf olay deseni, kaynak nesnenin ömrünü dinleyicisinin yararlı nesne yaşam süresi değerini aştığında de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd992-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="cd992-118">(Bu durumda, *yararlı* sizin tarafından belirlenir.) Zayıf olay deseni için kaydolun ve nesne yaşam süresi özellikleri herhangi bir şekilde dinleyicinin etkilemeden olay almak dinleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd992-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="cd992-119">Aslında, kaynak dolaylı başvuru dinleyici çöp toplama işlemi için uygun olup olmadığını belirlemez.</span><span class="sxs-lookup"><span data-stu-id="cd992-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="cd992-120">Bu nedenle zayıf olay deseni ve ilgili adlandırma zayıf bir başvuru başvurudur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd992-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="cd992-121">Dinleyici atık toplanan veya yok olabilir ve kaynak toplanamayan işleyici başvuruları artık yok edilmiş nesne korumadan devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd992-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="cd992-122">Zayıf olay deseni uygular kim?</span><span class="sxs-lookup"><span data-stu-id="cd992-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="cd992-123">Zayıf olay deseni uygulama öncelikli olarak denetim yazarları için ilginç.</span><span class="sxs-lookup"><span data-stu-id="cd992-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="cd992-124">Bir denetim yazarı olarak kapsama, Denetim ve takılı olduğundan uygulamaları olan etkisini ve davranışı için büyük ölçüde sorumlu olursunuz.</span><span class="sxs-lookup"><span data-stu-id="cd992-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="cd992-125">Bu denetim nesne yaşam süresi davranışı, özellikle açıklandığı gibi bir bellek sızıntısı sorununu işlenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd992-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="cd992-126">Belirli senaryolar kendiliğinden kendilerini zayıf olay deseni uygulamayı kiralamak.</span><span class="sxs-lookup"><span data-stu-id="cd992-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="cd992-127">Veri bağlama, böyle bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="cd992-127">One such scenario is data binding.</span></span> <span data-ttu-id="cd992-128">Veri bağlamasında, bağlama hedefi olan dinleyici nesnesinin tamamen bağımsız olarak kaynak nesnesi yaygındır.</span><span class="sxs-lookup"><span data-stu-id="cd992-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="cd992-129">Birçok yönden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama zaten sahip olayları nasıl uygulandığını içinde uygulanan zayıf olay deseni.</span><span class="sxs-lookup"><span data-stu-id="cd992-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="cd992-130">Zayıf olay deseni uygulama</span><span class="sxs-lookup"><span data-stu-id="cd992-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="cd992-131">Zayıf olay deseni uygulamak için üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cd992-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="cd992-132">Aşağıdaki tabloda, üç yaklaşımları listeler ve ne zaman kullanmanız gerektiği için bazı yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd992-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="cd992-133">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="cd992-133">Approach</span></span>|<span data-ttu-id="cd992-134">Ne zaman uygulanacağını</span><span class="sxs-lookup"><span data-stu-id="cd992-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="cd992-135">Varolan bir zayıf olay manager sınıfı kullanın</span><span class="sxs-lookup"><span data-stu-id="cd992-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="cd992-136">Abone olmak istediğiniz olayı karşılık gelen varsa <xref:System.Windows.WeakEventManager>, mevcut zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd992-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="cd992-137">WPF ile birlikte gelen zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cd992-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="cd992-138">Dahil edilen zayıf olay yöneticileri sınırlı olduğundan, diğer yaklaşımlar birini gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="cd992-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="cd992-139">Bir genel zayıf olay manager sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="cd992-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="cd992-140">Genel bir <xref:System.Windows.WeakEventManager%602> var <xref:System.Windows.WeakEventManager> kullanılabilir değilse, istediğiniz uygulama için kolay bir yol ve değilseniz verimliliği hakkında endişe duymaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd992-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="cd992-141">Genel <xref:System.Windows.WeakEventManager%602> bir mevcut veya özel zayıf olay Yöneticisi az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="cd992-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="cd992-142">Örneğin, genel bir sınıf olayın adı verilen olay bulmak için daha fazla yansıma yapar.</span><span class="sxs-lookup"><span data-stu-id="cd992-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="cd992-143">Ayrıca, olay genel kullanarak kaydetmek için kod <xref:System.Windows.WeakEventManager%602> daha var olan bir daha ayrıntılı veya özel <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="cd992-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="cd992-144">Özel bir zayıf olay manager sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd992-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="cd992-145">Bir özel Oluştur <xref:System.Windows.WeakEventManager> var <xref:System.Windows.WeakEventManager> kullanılabilir değil ve en iyi verim istiyor.</span><span class="sxs-lookup"><span data-stu-id="cd992-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="cd992-146">Özel bir kullanarak <xref:System.Windows.WeakEventManager> abone olmak için bir olay daha verimli olacaktır, ancak başına daha fazla kod yazmayı ücret.</span><span class="sxs-lookup"><span data-stu-id="cd992-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="cd992-147">Bir üçüncü taraf zayıf olay Yöneticisi'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="cd992-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="cd992-148">NuGet sahip [birkaç zayıf olay yöneticileri](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) ve birçok WPF çerçeveleri düzeni de destekler (örneği için bkz: [gevşek olay aboneliği Prism'ın belgelerine](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="cd992-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="cd992-149">Zayıf olay deseni uygulamak nasıl aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd992-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="cd992-150">Bu tartışma amacı doğrultusunda, olay abone olmak için aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd992-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="cd992-151">Olay adı `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="cd992-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="cd992-152">Olay tarafından gerçekleştirilen `EventSource` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cd992-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="cd992-153">Olay işleyicisinin türü vardır: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="cd992-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="cd992-154">Olay türünde bir parametre geçirir `SomeEventEventArgs` olay işleyicilerine.</span><span class="sxs-lookup"><span data-stu-id="cd992-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="cd992-155">Mevcut bir zayıf olay Manager sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="cd992-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd992-156">Mevcut bir zayıf olay Yöneticisi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="cd992-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="cd992-157">WPF ile birlikte gelen zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cd992-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="cd992-158">Normal olay birleştirme yerine yeni zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd992-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd992-159">Örneğin, kodunuz bir olaya abone olmak için şu desene kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd992-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd992-160">Bu da aşağıdaki deseni için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd992-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd992-161">Benzer şekilde, kodunuzu bir olayın aboneliğini kaldırmak için şu desene kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd992-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd992-162">Bu da aşağıdaki deseni için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd992-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="cd992-163">Genel zayıf olay Manager sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="cd992-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd992-164">Genel <xref:System.Windows.WeakEventManager%602> sınıfı yerine normal olay birleştirme.</span><span class="sxs-lookup"><span data-stu-id="cd992-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd992-165">Kullanırken <xref:System.Windows.WeakEventManager%602> olay dinleyicileri kaydetmek için olay kaynağı sağlamanız ve <xref:System.EventArgs> türü olarak sınıfı ve çağrı için tür parametreleri <xref:System.Windows.WeakEventManager%602.AddHandler%2A> aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="cd992-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="cd992-166">Özel bir zayıf olay Yöneticisi sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd992-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="cd992-167">Aşağıdaki sınıf şablonu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cd992-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="cd992-168">Bu sınıf devraldığı <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cd992-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="cd992-169">Değiştirin `SomeEventWeakEventManager` kendi adıyla adı.</span><span class="sxs-lookup"><span data-stu-id="cd992-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="cd992-170">Etkinliğiniz için karşılık gelen adları ile daha önce açıklanan üç adlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd992-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="cd992-171">(`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="cd992-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="cd992-172">Zayıf olay manager sınıfı görünürlüğünü (Genel / iç / özel) aynı görünürlük yönettiği olayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd992-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="cd992-173">Normal olay birleştirme yerine yeni zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd992-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="cd992-174">Örneğin, kodunuz bir olaya abone olmak için şu desene kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd992-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd992-175">Bu da aşağıdaki deseni için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd992-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="cd992-176">Benzer şekilde, kodunuz için bir olay aboneliği için şu desene kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="cd992-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="cd992-177">Bu da aşağıdaki deseni için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd992-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cd992-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd992-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="cd992-179">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd992-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="cd992-180">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd992-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
