---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181987"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="c605d-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="c605d-102">disconnectedContext MDA</span></span>
<span data-ttu-id="c605d-103">`disconnectedContext` Yönetilen hata ayıklama Yardımcısı (MDA), bir COM nesnesi ile ilgili bir istek bakım sırasında geçiş bağlantısı kesilen grubu veya bağlamı CLR girişiminde bulunduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c605d-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c605d-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c605d-104">Symptoms</span></span>  
 <span data-ttu-id="c605d-105">Üzerinde yapılan çağrıları bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) temel alınan bir COM bileşeni geçerli Grup ya da yerine, mevcut bir içerik teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="c605d-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="c605d-106">Bu, tek iş parçacıklı grup (STA) bileşenleri durumunda olduğu gibi birden çok iş parçacıklı COM bileşeni değilse bozulmasına ve/veya veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c605d-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="c605d-107">RCW kendisi bir proxy varsa, alternatif olarak, arama, atma neden olabilir bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile.</span><span class="sxs-lookup"><span data-stu-id="c605d-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c605d-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="c605d-108">Cause</span></span>  
 <span data-ttu-id="c605d-109">İçine geçişi CLR girişiminde bulunduğunda OLE grubu veya bağlamı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="c605d-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="c605d-110">Bu genellikle tüm grup tarafından sahip olunan COM bileşenleri tamamen olan bu serbest önce bilgisayarı Kapat kullanıcı kodundan bir RCW veya CLR, COM bileşeni düzenleme sırasında açık bir çağrı sonucu olarak ortaya çıkabilir STA apartmanlar kaynaklanır , örneğin, CLR serbest COM bileşeni ilişkili RCW atık bırakıldığında.</span><span class="sxs-lookup"><span data-stu-id="c605d-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c605d-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c605d-111">Resolution</span></span>  
 <span data-ttu-id="c605d-112">Bu sorunu önlemek için uygulama grupta Canlı tüm nesneleri ile bitmeden önce STA sahip iş parçacığının sonlanmamasına emin olun.</span><span class="sxs-lookup"><span data-stu-id="c605d-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="c605d-113">Aynı bağlamı için geçerlidir; uygulamanın bir bağlam içinde Canlı tüm COM bileşenlerini tamamen tamamlanmış olduğu önce bağlamları kapalı değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="c605d-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c605d-114">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="c605d-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="c605d-115">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c605d-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c605d-116">Yalnızca veri bağlantısı kesilen bağlam hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="c605d-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c605d-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c605d-117">Output</span></span>  
 <span data-ttu-id="c605d-118">Bağlantısı kesilen grubu veya bağlamı bağlam tanımlama bilgisini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c605d-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c605d-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c605d-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c605d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c605d-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c605d-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c605d-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c605d-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c605d-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
