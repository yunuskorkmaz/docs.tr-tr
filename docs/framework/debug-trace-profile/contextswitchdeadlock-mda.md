---
title: contextSwitchDeadlock MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 816afbae0cca18de24c11152541a509b54c119b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="1888b-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="1888b-102">contextSwitchDeadlock MDA</span></span>
<span data-ttu-id="1888b-103">`contextSwitchDeadlock` Yönetilen hata ayıklama Yardımcısı (MDA) bir kilitlenme denenen COM içerik geçişi sırasında algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1888b-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1888b-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1888b-104">Symptoms</span></span>  
 <span data-ttu-id="1888b-105">Yönetilen koddan yönetilmeyen bir COM bileşeni üzerinde bir çağrı döndürmez en yaygın belirti olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1888b-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="1888b-106">Başka bir belirti zaman içerisinde arttığını bellek kullanımı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1888b-106">Another symptom is memory usage increasing over time.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1888b-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="1888b-107">Cause</span></span>  
 <span data-ttu-id="1888b-108">Tek iş parçacıklı (STA) iş parçacığı iletileri Pompalama değil en olası nedeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1888b-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="1888b-109">STA iş parçacığı Pompalama olmadan ya da bekleme iletileri veya uzun işlemlerini gerçekleştirme ve pompa ileti kuyruğuna izin vermeyen ' dir.</span><span class="sxs-lookup"><span data-stu-id="1888b-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>  
  
 <span data-ttu-id="1888b-110">Çağrı girişimi sonlandırıcıyı iş parçacığı tarafından zaman içerisinde arttığını bellek kullanımı nedeniyle `Release` yönetilmeyen bir COM bileşeni ve bu bileşeni döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1888b-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="1888b-111">Bu, diğer nesneleri geri kazanma sonlandırıcıyı önler.</span><span class="sxs-lookup"><span data-stu-id="1888b-111">This prevents the finalizer from reclaiming other objects.</span></span>  
  
 <span data-ttu-id="1888b-112">Varsayılan olarak, Visual Basic konsol uygulamaları ana iş parçacığı için iş parçacığı modelini STA şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1888b-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="1888b-113">STA iş parçacığı COM birlikte çalışabilirliği doğrudan veya dolaylı olarak ortak dil çalışma zamanı veya bir üçüncü taraf denetim kullanıyorsa, bu MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1888b-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="1888b-114">Visual Basic konsol uygulamasındaki bu MDA etkinleştirmeyi önlemek için uygulama <xref:System.MTAThreadAttribute> özniteliği main yöntemini veya pompa iletileri uygulamaya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1888b-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>  
  
 <span data-ttu-id="1888b-115">Aşağıdaki koşulların hepsi gerçekleştiğinde yanlışlıkla etkinleştirilmesi ya da MDA mümkündür:</span><span class="sxs-lookup"><span data-stu-id="1888b-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="1888b-116">Uygulama COM bileşenlerini STA iş parçacıklarından kitaplıkları doğrudan veya dolaylı olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1888b-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>  
  
-   <span data-ttu-id="1888b-117">Uygulama Hata Ayıklayıcısı'ndaki durduruldu ve kullanıcı uygulamayı devam veya bir adım işlemi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1888b-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>  
  
-   <span data-ttu-id="1888b-118">Yönetilmeyen hata ayıklama etkin değil.</span><span class="sxs-lookup"><span data-stu-id="1888b-118">Unmanaged debugging is not enabled.</span></span>  
  
 <span data-ttu-id="1888b-119">MDA yanlışlıkla etkinleştirilip etkinleştirilmediğini belirlemek için tüm kesme noktaları devre dışı bırakmak, uygulamayı yeniden başlatın ve durmadan çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="1888b-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="1888b-120">MDA etkinleştirilmemişse, ilk etkinleştirme false olasıdır.</span><span class="sxs-lookup"><span data-stu-id="1888b-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="1888b-121">Bu durumda, mda'sı ile hata ayıklama oturumu önlemek için devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="1888b-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1888b-122">Bu mda'sı için varsayılan olarak [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="1888b-122">This MDA is in the default set for [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and later versions.</span></span> <span data-ttu-id="1888b-123">İçinde barındırma işlemi etkinleştirildiğinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], varsayılan olarak ayarlanmış olan Mda'lar devre dışı bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1888b-123">When the hosting process is enabled in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you cannot disable MDAs that are in the default set.</span></span> <span data-ttu-id="1888b-124">Barındırma işlemi varsayılan olarak etkindir, bu nedenle açıkça devre dışı bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1888b-124">The hosting process is enabled by default, so it must be explicitly disabled.</span></span> <span data-ttu-id="1888b-125">Mda'lar devre dışı bırakma hakkında daha fazla bilgi için bkz: "Mda'lar etkinleştirme ve devre dışı bırakma" [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="1888b-125">For information about how to disable MDAs, see "Enabling and Disabling MDAs" in [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1888b-126">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1888b-126">Resolution</span></span>  
 <span data-ttu-id="1888b-127">STA ileti Pompalama ilgili COM kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="1888b-127">Follow COM rules regarding STA message pumping.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1888b-128">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="1888b-128">Effect on the Runtime</span></span>  
 <span data-ttu-id="1888b-129">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1888b-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1888b-130">Yalnızca veri COM bağlamları hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="1888b-130">It only reports data about COM contexts.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1888b-131">Çıkış</span><span class="sxs-lookup"><span data-stu-id="1888b-131">Output</span></span>  
 <span data-ttu-id="1888b-132">Geçerli içerik ve hedef bağlamı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="1888b-132">A message describing the current context and the target context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1888b-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1888b-133">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1888b-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1888b-134">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="1888b-135">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1888b-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1888b-136">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1888b-136">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
