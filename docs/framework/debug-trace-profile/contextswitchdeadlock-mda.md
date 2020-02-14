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
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217552"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="7e6ce-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="7e6ce-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="7e6ce-103">`contextSwitchDeadlock` yönetilen hata ayıklama Yardımcısı (MDA), denenen bir COM bağlam geçişi sırasında kilitlenme algılandığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="7e6ce-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7e6ce-104">Symptoms</span></span>

<span data-ttu-id="7e6ce-105">En yaygın belirti, yönetilmeyen bir COM bileşenindeki bir çağrının yönetilen koddan döndürülmeidir.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="7e6ce-106">Başka bir belirti, zaman içinde artan bellek kullanımdır.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="7e6ce-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="7e6ce-107">Cause</span></span>

<span data-ttu-id="7e6ce-108">En olası neden, tek iş parçacıklı bir apartman (STA) iş parçacığının ileti pompalama.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="7e6ce-109">STA iş parçacığı, pompalama iletileri olmadan bekliyor ya da uzun işlemler gerçekleştiriyor ve ileti sırasının göndericmesine izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="7e6ce-110">Zaman içinde artan bellek kullanımı, yönetilmeyen bir COM bileşeni üzerinde `Release` çağırmaya çalışan Sonlandırıcı iş parçacığı nedeniyle oluşur ve bu bileşen dönmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="7e6ce-111">Bu, sonlandırıcının geri kazanma diğer nesnelerden yapılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="7e6ce-112">Varsayılan olarak, Visual Basic konsol uygulamalarının ana iş parçacığı için iş parçacığı modeli STA ' dır.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="7e6ce-113">Bir STA iş parçacığı ortak dil çalışma zamanı veya üçüncü taraf bir denetim aracılığıyla doğrudan veya dolaylı olarak COM birlikte çalışabilirliği kullanıyorsa, bu MDA etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="7e6ce-114">Bu MDA öğesini bir Visual Basic konsol uygulamasında etkinleştirmeyi önlemek için, <xref:System.MTAThreadAttribute> özniteliğini Main yöntemine uygulayın veya uygulamayı pompa iletileri olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="7e6ce-115">Aşağıdaki koşulların tümü karşılandığında bu MDA 'ın daha seyrek etkinleştirilmesi mümkündür:</span><span class="sxs-lookup"><span data-stu-id="7e6ce-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="7e6ce-116">Uygulama, doğrudan veya dolaylı olarak kitaplıklar aracılığıyla STA iş parçacıklarında COM bileşenleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="7e6ce-117">Uygulama hata ayıklayıcıda durduruldu ve Kullanıcı uygulamayı devam ettirdi ya da bir adım işlemi gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="7e6ce-118">Yönetilmeyen hata ayıklama etkin değil.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="7e6ce-119">MDA 'ın daha seyrek olarak etkinleştirildiğini anlamak için, tüm kesme noktalarını devre dışı bırakın, uygulamayı yeniden başlatın ve durmadan çalışmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="7e6ce-120">MDA etkinleştirilmemişse, ilk etkinleştirmenin yanlış olması olasıdır.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="7e6ce-121">Bu durumda, hata ayıklama oturumunda parazit önlemek için MDA ' ı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="7e6ce-122">Bu MDA, Visual Studio için varsayılan kümesidir.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="7e6ce-123">MDAs 'yi devre dışı bırakma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="7e6ce-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="7e6ce-124">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7e6ce-124">Resolution</span></span>

<span data-ttu-id="7e6ce-125">STA iletisi pompalama ile ilgili COM kurallarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="7e6ce-126">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="7e6ce-126">Effect on the Runtime</span></span>

<span data-ttu-id="7e6ce-127">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7e6ce-128">Yalnızca COM bağlamlarına ilişkin verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="7e6ce-129">Çıktı</span><span class="sxs-lookup"><span data-stu-id="7e6ce-129">Output</span></span>

<span data-ttu-id="7e6ce-130">Geçerli bağlamı ve hedef bağlamını açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="7e6ce-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7e6ce-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="7e6ce-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e6ce-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7e6ce-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7e6ce-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7e6ce-134">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7e6ce-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
