---
title: Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 330dc5ec76fe33a7f6165857334a367f578840ef
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="98f74-102">Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme</span><span class="sxs-lookup"><span data-stu-id="98f74-102">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="98f74-103">Olay tabanlı zaman uyumsuz desen bir sınıfı zaman uyumsuz davranışı sunmaya yönelik bir desen sağlar.</span><span class="sxs-lookup"><span data-stu-id="98f74-103">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="98f74-104">Bu desen girişiyle [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz davranışı gösterme için iki modeli tanımlar: zaman uyumsuz desen dayalı <xref:System.IAsyncResult?displayProperty=nameWithType> arabirimi ve olay tabanlı düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-104">With the introduction of this pattern, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="98f74-105">Bu konu, her iki desenlerini uygulama için uygun olduğunda açıklar.</span><span class="sxs-lookup"><span data-stu-id="98f74-105">This topic describes when it is appropriate for you to implement both patterns.</span></span>  
  
 <span data-ttu-id="98f74-106">İle zaman uyumsuz programlama hakkında daha fazla bilgi için <xref:System.IAsyncResult> arabirim için bkz: [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="98f74-106">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
## <a name="general-principles"></a><span data-ttu-id="98f74-107">Genel ilkeler</span><span class="sxs-lookup"><span data-stu-id="98f74-107">General Principles</span></span>  
 <span data-ttu-id="98f74-108">Genel olarak, olay tabanlı zaman uyumsuz desen mümkün olduğunca kullanarak zaman uyumsuz özellikler maruz bırakmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="98f74-108">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="98f74-109">Ancak, olay tabanlı deseni karşılayamayan bazı gereksinimler vardır.</span><span class="sxs-lookup"><span data-stu-id="98f74-109">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="98f74-110">Bu durumda, uygulamanız gerekebilir <xref:System.IAsyncResult> olay tabanlı deseni yanı sıra düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-110">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98f74-111">Nadir <xref:System.IAsyncResult> da uygulanan olay tabanlı deseni uygulanması için desen.</span><span class="sxs-lookup"><span data-stu-id="98f74-111">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="98f74-112">Kuralları</span><span class="sxs-lookup"><span data-stu-id="98f74-112">Guidelines</span></span>  
 <span data-ttu-id="98f74-113">Aşağıdaki liste, olay tabanlı zaman uyumsuz desenin ne zaman uygulamak için yönergeleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="98f74-113">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>  
  
-   <span data-ttu-id="98f74-114">Olay tabanlı deseni varsayılan API sınıfınız için zaman uyumsuz davranışı kullanıma sunmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="98f74-114">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>  
  
-   <span data-ttu-id="98f74-115">Değil kullanıma <xref:System.IAsyncResult> desen sınıfınız öncelikle bir istemci uygulaması, örneğin Windows Forms kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="98f74-115">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>  
  
-   <span data-ttu-id="98f74-116">Yalnızca kullanıma <xref:System.IAsyncResult> desen gereksinimlerinizi karşılamak için gerekli olduğunda.</span><span class="sxs-lookup"><span data-stu-id="98f74-116">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="98f74-117">Örneğin, var olan bir API ile uyumluluk kullanıma sunmak gerektirebilecek <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-117">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="98f74-118">Değil kullanıma <xref:System.IAsyncResult> ayrıca olay tabanlı deseni gösterme olmadan düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-118">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>  
  
-   <span data-ttu-id="98f74-119">Kullanıma gerekir, <xref:System.IAsyncResult> desen, Gelişmiş bir seçenek olarak bunu.</span><span class="sxs-lookup"><span data-stu-id="98f74-119">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="98f74-120">Proxy nesnesi oluşturursanız, örneğin, olay tabanlı deseni oluşturmak için bir seçenek ile varsayılan üretmek <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-120">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="98f74-121">Olay tabanlı deseni uygulamanızı oluşturmak, <xref:System.IAsyncResult> desen uygulaması.</span><span class="sxs-lookup"><span data-stu-id="98f74-121">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>  
  
-   <span data-ttu-id="98f74-122">Her iki olay tabanlı deseni kullanılmasını önlemek ve <xref:System.IAsyncResult> düzeni aynı sınıfta.</span><span class="sxs-lookup"><span data-stu-id="98f74-122">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="98f74-123">Olay tabanlı deseni "daha yüksek düzey" sınıflarda kullanıma ve <xref:System.IAsyncResult> üzerinde "düzeyini düşürmek" sınıfların desen.</span><span class="sxs-lookup"><span data-stu-id="98f74-123">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="98f74-124">Örneğin, olay tabanlı deseni üzerinde karşılaştırmak <xref:System.Net.WebClient> ile bileşen <xref:System.IAsyncResult> üzerinde desen <xref:System.Web.HttpRequest> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="98f74-124">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>  
  
    -   <span data-ttu-id="98f74-125">Olay tabanlı deseni kullanıma ve <xref:System.IAsyncResult> düzeni uyumluluk gerektirdiğinde aynı sınıfta.</span><span class="sxs-lookup"><span data-stu-id="98f74-125">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="98f74-126">Örneğin, kullanan bir API zaten yayımlandı <xref:System.IAsyncResult> desen korumak gerekir <xref:System.IAsyncResult> geriye dönük uyumluluk için desen.</span><span class="sxs-lookup"><span data-stu-id="98f74-126">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>  
  
    -   <span data-ttu-id="98f74-127">Olay tabanlı deseni kullanıma ve <xref:System.IAsyncResult> elde edilen nesne modeli karmaşıklık uygulamaları ayırma avantajı ağır varsa aynı sınıf içinde desen.</span><span class="sxs-lookup"><span data-stu-id="98f74-127">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="98f74-128">Olay tabanlı deseni kullanılmasını önlemek üzere daha tek bir sınıftaki her iki desenleri kullanıma sunmak iyidir.</span><span class="sxs-lookup"><span data-stu-id="98f74-128">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>  
  
    -   <span data-ttu-id="98f74-129">Her iki olay tabanlı deseni kullanıma varsa ve <xref:System.IAsyncResult> kullanım tek bir sınıf desenine <xref:System.ComponentModel.EditorBrowsableAttribute> kümesine <xref:System.ComponentModel.EditorBrowsableState.Advanced> işaretlemek için <xref:System.IAsyncResult> Gelişmiş bir özellik olarak düzeni uygulaması.</span><span class="sxs-lookup"><span data-stu-id="98f74-129">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="98f74-130">Bu gibi görüntüleme için Visual Studio IntelliSense, tasarım ortamlara gösterir <xref:System.IAsyncResult> özellikleri ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="98f74-130">This indicates to design environments, such as Visual Studio IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="98f74-131">Bu özellikleri ve yöntemleri hala tam olarak kullanılabilir, ancak IntelliSense çalışan Geliştirici API daha anlaşılır bir görünüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98f74-131">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="98f74-132">Olay tabanlı deseni yanı sıra IAsyncResult düzeni gösterme ölçütleri</span><span class="sxs-lookup"><span data-stu-id="98f74-132">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>  
 <span data-ttu-id="98f74-133">Olay tabanlı zaman uyumsuz desen yukarıda açıklanan senaryoları altında birçok avantaj sahipken, performans, en önemli gereksinimi varsa bilmeniz gereken bazı dezavantajları sahip.</span><span class="sxs-lookup"><span data-stu-id="98f74-133">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>  
  
 <span data-ttu-id="98f74-134">Olay tabanlı deseni olmayan adres üç senaryo vardır yanı sıra <xref:System.IAsyncResult> Desen:</span><span class="sxs-lookup"><span data-stu-id="98f74-134">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="98f74-135">Bir bekleme engelleme <xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="98f74-135">Blocking wait on one <xref:System.IAsyncResult></span></span>  
  
-   <span data-ttu-id="98f74-136">Birçok bekleme engelleme <xref:System.IAsyncResult> nesneleri</span><span class="sxs-lookup"><span data-stu-id="98f74-136">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>  
  
-   <span data-ttu-id="98f74-137">Üzerinde tamamlanması için yoklama <xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="98f74-137">Polling for completion on the <xref:System.IAsyncResult></span></span>  
  
 <span data-ttu-id="98f74-138">Olay tabanlı deseni kullanarak bu senaryoyu ele, ancak bunun yapılması kullanmaktan daha kullanışsız <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-138">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>  
  
 <span data-ttu-id="98f74-139">Geliştiriciler sık kullandığınız <xref:System.IAsyncResult> genellikle çok yüksek performans gereksinimlerin Hizmetleri için desen.</span><span class="sxs-lookup"><span data-stu-id="98f74-139">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="98f74-140">Örneğin, yoklama tamamlama senaryosu için yüksek performanslı sunucu tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="98f74-140">For example, the polling for completion scenario is a high-performance server technique.</span></span>  
  
 <span data-ttu-id="98f74-141">Ayrıca, olay tabanlı deseni daha az verimli <xref:System.IAsyncResult> daha fazla nesneleri, özellikle oluşturduğundan desen <xref:System.EventArgs>, ve iş parçacıkları arasında eşitler.</span><span class="sxs-lookup"><span data-stu-id="98f74-141">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>  
  
 <span data-ttu-id="98f74-142">Aşağıdaki liste kullanmaya karar verirseniz izlemek için bazı öneriler gösterir <xref:System.IAsyncResult> Desen:</span><span class="sxs-lookup"><span data-stu-id="98f74-142">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="98f74-143">Yalnızca kullanıma <xref:System.IAsyncResult> desen desteği özellikle gerektirdiğinde <xref:System.Threading.WaitHandle> veya <xref:System.IAsyncResult> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="98f74-143">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>  
  
-   <span data-ttu-id="98f74-144">Yalnızca kullanıma <xref:System.IAsyncResult> desen kullanan mevcut bir API olduğunda <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-144">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="98f74-145">Temel bir varolan API varsa <xref:System.IAsyncResult> desen, ayrıca, bir sonraki sürümde olay tabanlı deseni gösterme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="98f74-145">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>  
  
-   <span data-ttu-id="98f74-146">Yalnızca kullanıma <xref:System.IAsyncResult> doğrulandı yüksek performans gereksinimlerini varsa düzeni olay tabanlı bir desen karşılanamıyor ancak tarafından karşılanması <xref:System.IAsyncResult> düzeni.</span><span class="sxs-lookup"><span data-stu-id="98f74-146">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f74-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98f74-147">See Also</span></span>  
 [<span data-ttu-id="98f74-148">İzlenecek yol: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="98f74-148">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="98f74-149">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="98f74-149">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="98f74-150">Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama</span><span class="sxs-lookup"><span data-stu-id="98f74-150">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="98f74-151">Olay Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="98f74-151">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="98f74-152">Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98f74-152">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="98f74-153">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98f74-153">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
