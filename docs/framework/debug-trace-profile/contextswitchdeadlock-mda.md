---
title: contextSwitchDeadlock MDA
description: Bir COM bağlam geçişi sırasında kilitlenme algılandığında etkinleştirilen, .NET 'teki Contextswitchkilitlenme yönetilen hata ayıklama Yardımcısı (MDA) hakkında bilgi edinin.
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
ms.openlocfilehash: 52db4f2c88bac4e8cac621cca989fa10acb43f94
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416024"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="703b4-103">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="703b4-103">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="703b4-104">`contextSwitchDeadlock`Yönetilen hata ayıklama Yardımcısı (MDA), denenen BIR com bağlam geçişi sırasında bir kilitlenme algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="703b4-104">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="703b4-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="703b4-105">Symptoms</span></span>

<span data-ttu-id="703b4-106">En yaygın belirti, yönetilmeyen bir COM bileşenindeki bir çağrının yönetilen koddan döndürülmeidir.</span><span class="sxs-lookup"><span data-stu-id="703b4-106">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="703b4-107">Başka bir belirti, zaman içinde artan bellek kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="703b4-107">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="703b4-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="703b4-108">Cause</span></span>

<span data-ttu-id="703b4-109">En olası neden, tek iş parçacıklı bir apartman (STA) iş parçacığının ileti pompalama.</span><span class="sxs-lookup"><span data-stu-id="703b4-109">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="703b4-110">STA iş parçacığı, pompalama iletileri olmadan bekliyor ya da uzun işlemler gerçekleştiriyor ve ileti sırasının göndericmesine izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="703b4-110">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="703b4-111">Zaman içinde artan bellek kullanımı, `Release` yönetilmeyen BIR COM bileşenini çağırmaya çalışan ve bu bileşen döndürülmeyen Sonlandırıcı iş parçacığı nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="703b4-111">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="703b4-112">Bu, sonlandırıcının geri kazanma diğer nesnelerden yapılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="703b4-112">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="703b4-113">Varsayılan olarak, Visual Basic konsol uygulamalarının ana iş parçacığı için iş parçacığı modeli STA ' dır.</span><span class="sxs-lookup"><span data-stu-id="703b4-113">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="703b4-114">Bir STA iş parçacığı ortak dil çalışma zamanı veya üçüncü taraf bir denetim aracılığıyla doğrudan veya dolaylı olarak COM birlikte çalışabilirliği kullanıyorsa, bu MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="703b4-114">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="703b4-115">Bu MDA öğesini bir Visual Basic konsol uygulamasında etkinleştirmeyi önlemek için, <xref:System.MTAThreadAttribute> özniteliği Main yöntemine uygulayın veya uygulamayı pompa iletileri olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="703b4-115">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="703b4-116">Aşağıdaki koşulların tümü karşılandığında bu MDA 'ın daha seyrek etkinleştirilmesi mümkündür:</span><span class="sxs-lookup"><span data-stu-id="703b4-116">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="703b4-117">Uygulama, doğrudan veya dolaylı olarak kitaplıklar aracılığıyla STA iş parçacıklarında COM bileşenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="703b4-117">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="703b4-118">Uygulama hata ayıklayıcıda durduruldu ve Kullanıcı uygulamayı devam ettirdi ya da bir adım işlemi gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="703b4-118">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="703b4-119">Yönetilmeyen hata ayıklama etkin değil.</span><span class="sxs-lookup"><span data-stu-id="703b4-119">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="703b4-120">MDA 'ın daha seyrek olarak etkinleştirildiğini anlamak için, tüm kesme noktalarını devre dışı bırakın, uygulamayı yeniden başlatın ve durmadan çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="703b4-120">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="703b4-121">MDA etkinleştirilmemişse, ilk etkinleştirmenin yanlış olması olasıdır.</span><span class="sxs-lookup"><span data-stu-id="703b4-121">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="703b4-122">Bu durumda, hata ayıklama oturumunda parazit önlemek için MDA ' ı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="703b4-122">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="703b4-123">Bu MDA, Visual Studio için varsayılan kümesidir.</span><span class="sxs-lookup"><span data-stu-id="703b4-123">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="703b4-124">MDAs 'yi devre dışı bırakma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="703b4-124">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="703b4-125">Çözüm</span><span class="sxs-lookup"><span data-stu-id="703b4-125">Resolution</span></span>

<span data-ttu-id="703b4-126">STA iletisi pompalama ile ilgili COM kurallarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="703b4-126">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="703b4-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="703b4-127">Effect on the Runtime</span></span>

<span data-ttu-id="703b4-128">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="703b4-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="703b4-129">Yalnızca COM bağlamlarına ilişkin verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="703b4-129">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="703b4-130">Çıktı</span><span class="sxs-lookup"><span data-stu-id="703b4-130">Output</span></span>

<span data-ttu-id="703b4-131">Geçerli bağlamı ve hedef bağlamını açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="703b4-131">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="703b4-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="703b4-132">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="703b4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="703b4-133">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="703b4-134">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="703b4-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="703b4-135">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="703b4-135">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
