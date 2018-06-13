---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 4b1e8649e5d550ffa2c7ee614cb9102f86a83ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549353"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="9ec41-102">Zayıf Olay Desenleri</span><span class="sxs-lookup"><span data-stu-id="9ec41-102">Weak Event Patterns</span></span>
<span data-ttu-id="9ec41-103">Uygulamalarda, olay kaynaklarına bağlı işleyicileri işleyici kaynağına eklenen dinleyici nesne birlikte yok edilmeyecek olduğunu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9ec41-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="9ec41-104">Bu durum bellek sızıntıları yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="9ec41-105"> belirli olaylar için ayrılmış yönetici sınıfı sağlayarak ve bu olay için dinleyiciler üzerinde arabirimi uygulama bu sorunu gidermek için kullanılan bir tasarım desenini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="9ec41-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="9ec41-106">Bu tasarım deseni olarak bilinen *zayıf olay deseni*.</span><span class="sxs-lookup"><span data-stu-id="9ec41-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="9ec41-107">Neden zayıf olay deseni uygulansın mı?</span><span class="sxs-lookup"><span data-stu-id="9ec41-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="9ec41-108">Olayları dinleme bellek sızıntıları yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="9ec41-109">Bir olayı dinlemek için tipik teknik kaynak üzerinde bir olay işleyici iliştirir dile özgü sözdizimi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9ec41-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="9ec41-110">Örneğin, C# ' ta o sözdizimi şöyledir: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="9ec41-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="9ec41-111">Bu teknik güçlü bir başvuru olay kaynağından olay dinleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="9ec41-112">Normalde, olay işleyicisi için bir dinleyici ekleme (olay işleyicisi açıkça kaldırılmadığı sürece), kaynak nesne ömrü tarafından etkileyen bir nesne ömrü dinleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="9ec41-113">Ancak bazı durumlarda olup şu anda görsel ağaç uygulamanın ve kaynak ömrü tarafından ait olduğu gibi diğer faktörler tarafından denetlenmesi için dinleyici nesne ömrü isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ec41-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="9ec41-114">Kaynak nesne ömrü dinleyici nesne ömrü genişletir olduğunda, normal olay deseni bir bellek sızıntısı müşteri adayları: dinleyici istenenden daha uzun süre Canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="9ec41-115">Zayıf olay deseni bu bellek sızıntısı sorununu çözmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9ec41-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="9ec41-116">Zayıf olay düzeni için bir olay kaydetmek bir dinleyici gerekiyor, ancak ne zaman kaydı dinleyicisi açıkça bilmez olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="9ec41-117">Kaynak nesne ömrü dinleyicisinin yararlı nesne ömrü aştığında zayıf olay düzeni de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="9ec41-118">(Bu durumda, *yararlı* tarafından belirlenir.) Zayıf olay deseni kaydolun ve herhangi bir şekilde dinleyici nesne ömrü özelliklerini etkilemeden olay almak dinleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ec41-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="9ec41-119">Etkin dolaylı başvuru kaynağından dinleyici atık toplama için uygun olup olmadığını belirlemez.</span><span class="sxs-lookup"><span data-stu-id="9ec41-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="9ec41-120">Bu nedenle zayıf olay düzeni ve ilgili adlandırma zayıf bir başvuru başvurudur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ec41-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="9ec41-121">Dinleyici toplanan veya aksi halde yok çöp olabilir ve kaynağı artık yok nesnesine olan toplanamayan işleyici başvurularını korumadan devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="9ec41-122">Kimin zayıf olay desenini uygular?</span><span class="sxs-lookup"><span data-stu-id="9ec41-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="9ec41-123">Zayıf olay düzeni uygulama öncelikle denetim yazarları için ilginç olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9ec41-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="9ec41-124">Denetim yazarı olarak, büyük ölçüde davranış ve kapsama denetiminizi ve takılı olduğundan uygulamaları sahip etkisi sorumludur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="9ec41-125">Bu nesne yaşam süresi davranışını denetlemeye özellikle açıklanan bellek sızıntısı sorununu işlenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="9ec41-126">Belirli senaryolar kendiliğinden kendilerini zayıf olay deseni uygulamaya ödünç.</span><span class="sxs-lookup"><span data-stu-id="9ec41-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="9ec41-127">Bu senaryolardan biri, veri bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-127">One such scenario is data binding.</span></span> <span data-ttu-id="9ec41-128">Veri bağlama, kaynak nesnenin bir bağlama hedefidir dinleyici nesne tamamen bağımsız olması için yaygın bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="9ec41-129">Pek çok görünüşünün [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri zaten bağlama sahip olayları nasıl uygulandığı durumunda uygulanan zayıf olay deseni.</span><span class="sxs-lookup"><span data-stu-id="9ec41-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="9ec41-130">Zayıf olay deseni nasıl uygulanır</span><span class="sxs-lookup"><span data-stu-id="9ec41-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="9ec41-131">Zayıf olay desen uygulamak için üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="9ec41-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="9ec41-132">Aşağıdaki tabloda, üç yaklaşımlar listeler ve her zaman kullanmalısınız için bazı yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ec41-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="9ec41-133">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="9ec41-133">Approach</span></span>|<span data-ttu-id="9ec41-134">Ne zaman uygulanacağını</span><span class="sxs-lookup"><span data-stu-id="9ec41-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="9ec41-135">Varolan bir zayıf olay Yöneticisi sınıfı kullanın</span><span class="sxs-lookup"><span data-stu-id="9ec41-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="9ec41-136">Abone olmak istediğiniz olayı karşılık gelen varsa <xref:System.Windows.WeakEventManager>, varolan zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="9ec41-137">WPF ile birlikte zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="9ec41-138">Ancak, büyük olasılıkla diğer yaklaşımlardan birini seçmeniz gerekir, böylece WPF ile birlikte nispeten az zayıf olay yöneticileri olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="9ec41-139">Bir genel zayıf olay Yöneticisi sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="9ec41-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="9ec41-140">Genel kullanmak <xref:System.Windows.WeakEventManager%602> var olan <xref:System.Windows.WeakEventManager> verimliliği hakkında kullanılabilir değil, uygulama için kolay bir yol istediğiniz ve değildir ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="9ec41-141">Genel <xref:System.Windows.WeakEventManager%602> bir mevcut veya özel zayıf olay Yöneticisi daha az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="9ec41-142">Örneğin, genel bir sınıf olayın adı verilen olay bulmak için daha fazla yansıma yapar.</span><span class="sxs-lookup"><span data-stu-id="9ec41-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="9ec41-143">Ayrıca, olay genel kullanarak kaydetmek için kod <xref:System.Windows.WeakEventManager%602> daha ayrıntılı varolan kullanmaktan veya özel <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="9ec41-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="9ec41-144">Özel zayıf olay Yöneticisi sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ec41-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="9ec41-145">Bir özel Oluştur <xref:System.Windows.WeakEventManager> var olan <xref:System.Windows.WeakEventManager> kullanılabilir değil ve en iyi verim istiyor.</span><span class="sxs-lookup"><span data-stu-id="9ec41-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="9ec41-146">Özel bir kullanarak <xref:System.Windows.WeakEventManager> abone olmak için bir olay daha verimli olacaktır, ancak başına daha fazla kod yazmaya maliyet doğurur.</span><span class="sxs-lookup"><span data-stu-id="9ec41-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="9ec41-147">Aşağıdaki bölümlerde zayıf olay deseni uygulayan açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ec41-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="9ec41-148">Bu tartışma amaçları doğrultusunda, Abone olunacak olay aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9ec41-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="9ec41-149">Olay adı `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="9ec41-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="9ec41-150">Olay tarafından tetiklenir `EventSource` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="9ec41-151">Olay işleyicisinin türü vardır: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="9ec41-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="9ec41-152">Olay türünü parametre olarak geçirir `SomeEventEventArgs` olay işleyicileri için.</span><span class="sxs-lookup"><span data-stu-id="9ec41-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="9ec41-153">Varolan bir zayıf olay Yöneticisi sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="9ec41-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="9ec41-154">Varolan bir zayıf olay Yöneticisi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="9ec41-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="9ec41-155">WPF ile birlikte zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="9ec41-156">Normal olay bağlantı yerine yeni zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9ec41-157">Örneğin, kodunuzu bir olaya abone olmak için aşağıdaki düzeni kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="9ec41-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9ec41-158">Aşağıdaki desenini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ec41-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9ec41-159">Benzer şekilde, kodunuzu bir olaya aboneliğinizi iptal etmek için aşağıdaki düzeni kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="9ec41-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="9ec41-160">Aşağıdaki desenini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ec41-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="9ec41-161">Genel zayıf olay Yöneticisi sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="9ec41-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="9ec41-162">Genel kullanmak <xref:System.Windows.WeakEventManager%602> normal olay bağlantı yerine sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9ec41-163">Kullandığınızda <xref:System.Windows.WeakEventManager%602> olay dinleyicileri kaydetmek için olay kaynağı tedarik ve <xref:System.EventArgs> türü sınıfı ve çağrı türü parametreleri olarak <xref:System.Windows.WeakEventManager%602.AddHandler%2A> aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="9ec41-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="9ec41-164">Özel bir zayıf olay Yöneticisi sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ec41-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="9ec41-165">Aşağıdaki sınıf şablonu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="9ec41-166">Bu sınıf devraldığı <xref:System.Windows.WeakEventManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="9ec41-167">Değiştir `SomeEventWeakEventManager` kendi adıyla adı.</span><span class="sxs-lookup"><span data-stu-id="9ec41-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="9ec41-168">Olayınızın ilişkili adlarıyla daha önce açıklanan üç adlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9ec41-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="9ec41-169">(`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="9ec41-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="9ec41-170">Zayıf olay Yöneticisi sınıfı görünürlüğünü (ortak / iç / özel) aynı görünürlük yönettiği olayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="9ec41-171">Normal olay bağlantı yerine yeni zayıf olay Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ec41-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9ec41-172">Örneğin, kodunuzu bir olaya abone olmak için aşağıdaki düzeni kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="9ec41-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9ec41-173">Aşağıdaki desenini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ec41-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9ec41-174">Benzer şekilde, kodunuzu bir olaya aboneliğinizi iptal etmek için aşağıdaki düzeni kullanıyorsa:</span><span class="sxs-lookup"><span data-stu-id="9ec41-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="9ec41-175">Aşağıdaki desenini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ec41-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9ec41-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec41-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="9ec41-177">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ec41-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="9ec41-178">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ec41-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
