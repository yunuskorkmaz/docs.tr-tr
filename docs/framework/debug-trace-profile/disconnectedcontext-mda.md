---
title: disconnectedContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e840fc24361735b65879702293daadce0bc90e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="38a14-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="38a14-102">disconnectedContext MDA</span></span>
<span data-ttu-id="38a14-103">`disconnectedContext` Yönetilen hata ayıklama Yardımcısı (MDA) bir COM nesnesi ile ilgili bir istek bakım sırasında geçiş bağlantısı kesilen grubu veya bağlamı CLR girişiminde bulunduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="38a14-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38a14-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="38a14-104">Symptoms</span></span>  
 <span data-ttu-id="38a14-105">Üzerinde yapılan çağrılar bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) geçerli grubu veya bağlamı yerine, mevcut bir temel alınan COM bileşeni teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="38a14-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="38a14-106">COM bileşeni, tek iş parçacıklı (STA) bileşenleri durumda olduğu gibi birden çok iş parçacıklı değilse bu bozulması ve/veya veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="38a14-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="38a14-107">RCW kendisini bir proxy ise, alternatif olarak, arama, atma sonuçlanabilir bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile.</span><span class="sxs-lookup"><span data-stu-id="38a14-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38a14-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="38a14-108">Cause</span></span>  
 <span data-ttu-id="38a14-109">Geçiş içine CLR girişiminde bulunduğunda OLE grubu veya bağlamı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="38a14-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="38a14-110">Bunun en yaygın olarak tüm grup tarafından sahip olunan COM bileşenleri tamamen olan bu serbest önce bilgisayarı Kapat kullanıcı kodundan bir RCW veya COM bileşeni CLR işleme sırasında açık bir çağrı sonucu olarak ortaya çıkabilir STA grupların nedeni , örneğin ne zaman CLR serbest COM bileşeninin ilişkili RCW toplanan atık kaldığında.</span><span class="sxs-lookup"><span data-stu-id="38a14-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38a14-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="38a14-111">Resolution</span></span>  
 <span data-ttu-id="38a14-112">Bu sorunu önlemek için uygulama grupta Canlı tüm nesneler bitmeden önce STA sahip iş parçacığı sonlandırma değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="38a14-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="38a14-113">Aynı bağlamları için geçerlidir; uygulama bağlamı içinde dinamik herhangi COM bileşenleri ile tamamen tamamlanmış önce bağlamları kapalı değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="38a14-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38a14-114">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="38a14-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="38a14-115">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="38a14-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="38a14-116">Yalnızca veri bağlantısı kesilen bağlam hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="38a14-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38a14-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="38a14-117">Output</span></span>  
 <span data-ttu-id="38a14-118">Bağlantısı kesilen grubu veya bağlamı bağlam tanımlama bilgisini raporlar.</span><span class="sxs-lookup"><span data-stu-id="38a14-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="38a14-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="38a14-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38a14-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38a14-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="38a14-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="38a14-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="38a14-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="38a14-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
