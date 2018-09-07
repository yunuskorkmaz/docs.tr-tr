---
title: contextSwitchDeadlock MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdbad4a5eb9a9d0c81ae8d29394652e9f6df136e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046177"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="8409b-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="8409b-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="8409b-103">`contextSwitchDeadlock` Denenen bir COM içerik geçişi sırasında karşılıklı bir kilitlenme tespit edildiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8409b-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="8409b-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="8409b-104">Symptoms</span></span>

<span data-ttu-id="8409b-105">En yaygın yönetilen koddan yönetilmeyen COM bileşeni üzerinde bir çağrı döndürmez belirtisidir.</span><span class="sxs-lookup"><span data-stu-id="8409b-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="8409b-106">Zaman içinde artan bellek kullanımı başka bir belirtisidir.</span><span class="sxs-lookup"><span data-stu-id="8409b-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="8409b-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="8409b-107">Cause</span></span>

<span data-ttu-id="8409b-108">En olası nedeni, bir tek iş parçacıklı grup (STA) iş parçacığı iletileri Pompalama değil ' dir.</span><span class="sxs-lookup"><span data-stu-id="8409b-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="8409b-109">STA iş parçacığı Pompalama olmadan ya da bekleyen iletileri veya uzun işlemlerini gerçekleştirme ve ileti kuyruğuna pompa izin vermiyor ' dir.</span><span class="sxs-lookup"><span data-stu-id="8409b-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="8409b-110">Zaman içinde artan bellek kullanımı arama girişimi Sonlandırıcı iş parçacığı tarafından neden `Release` bir yönetilmeyen COM bileşeni ve söz konusu bileşen döndürmez.</span><span class="sxs-lookup"><span data-stu-id="8409b-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="8409b-111">Bu, sonlandırıcının diğer nesnelerin tekrar kullanılabilir hale engeller.</span><span class="sxs-lookup"><span data-stu-id="8409b-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="8409b-112">Varsayılan olarak, Visual Basic konsol uygulamaları ana iş parçacığı için iş parçacığı modeli STA. olur.</span><span class="sxs-lookup"><span data-stu-id="8409b-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="8409b-113">Bir STA iş parçacığı COM birlikte çalışabilirlik doğrudan veya dolaylı olarak ortak dil çalışma zamanı veya bir üçüncü taraf denetimi kullanıyorsa, bu mda'nın etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="8409b-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="8409b-114">Bir Visual Basic konsol uygulamasında bu MDA etkinleştirme önlemek için uygulama <xref:System.MTAThreadAttribute> özniteliğini main yöntemine veya iletileri göndermek için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8409b-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="8409b-115">Bu MDA aşağıdaki koşulların tümü karşılandığında, yanlışlıkla etkinleştirilecek mümkündür:</span><span class="sxs-lookup"><span data-stu-id="8409b-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

-   <span data-ttu-id="8409b-116">Bir uygulama STA iş parçacığı için COM bileşenlerini kitaplıkları doğrudan veya dolaylı olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8409b-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

-   <span data-ttu-id="8409b-117">Uygulama hata ayıklayıcıda durduruldu ve kullanıcı uygulamanın devam veya adım işlemi gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="8409b-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

-   <span data-ttu-id="8409b-118">Yönetilemeyen hata ayıklama etkin değil.</span><span class="sxs-lookup"><span data-stu-id="8409b-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="8409b-119">MDA yanlışlıkla etkinleştirilip etkinleştirilmediğini belirlemek için tüm kesme noktalarını devre dışı bırakmak, uygulamayı yeniden başlatın ve durmadan çalışmasına izin.</span><span class="sxs-lookup"><span data-stu-id="8409b-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="8409b-120">MDA etkinleştirilmemesi halinde ilk etkinleştirme false olasıdır.</span><span class="sxs-lookup"><span data-stu-id="8409b-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="8409b-121">Bu durumda, hata ayıklama oturumu ile önlemek için MDA devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="8409b-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="8409b-122">Bu mda'nın varsayılan Visual Studio için kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="8409b-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="8409b-123">Mda'leri devre dışı bırakma hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="8409b-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="8409b-124">Çözüm</span><span class="sxs-lookup"><span data-stu-id="8409b-124">Resolution</span></span>

<span data-ttu-id="8409b-125">STA ileti Pompalama ilgili COM kuralları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8409b-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="8409b-126">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="8409b-126">Effect on the Runtime</span></span>

<span data-ttu-id="8409b-127">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8409b-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8409b-128">Yalnızca veri COM bağlamları hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="8409b-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="8409b-129">Çıkış</span><span class="sxs-lookup"><span data-stu-id="8409b-129">Output</span></span>

<span data-ttu-id="8409b-130">Geçerli bağlamı ve hedef bağlamı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="8409b-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="8409b-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8409b-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="8409b-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8409b-132">See Also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8409b-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="8409b-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8409b-134">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="8409b-134">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
