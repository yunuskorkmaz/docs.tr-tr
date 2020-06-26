---
title: disconnectedContext MDA
description: CLR bağlantısı kesilen bir gruba veya içeriğe geçişe çalıştığında çağrılan .NET 'teki disconnectedContext yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416089"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="f1591-103">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="f1591-103">disconnectedContext MDA</span></span>
<span data-ttu-id="f1591-104">`disconnectedContext`Yönetilen hata ayıklama Yardımcısı (MDA), clr BIR com nesnesiyle ilgili bir isteğe hizmet verirken, bağlantısı kesilen bir gruba veya içeriğe geçişe çalıştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f1591-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f1591-105">Symptoms</span></span>  
 <span data-ttu-id="f1591-106">[Çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde yapılan çağrılar, mevcut grubun veya bağlamdaki temel alınan com bileşenine sahip oldukları bir yerine, geçerli grupta veya bağlamda dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="f1591-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="f1591-107">Bu, tek iş parçacıklı apartman (STA) bileşenlerinde olduğu gibi COM bileşeni çok iş parçacıklı değilse bozulma ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="f1591-108">Alternatif olarak, RCW kendisi bir ara sunucu ise, çağrı bir <xref:System.Runtime.InteropServices.COMException> HRESULT RPC_E_WRONG_THREAD ile birlikte Oluşturuma yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f1591-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f1591-109">Cause</span></span>  
 <span data-ttu-id="f1591-110">CLR kendisine geçişe çalıştığında OLE Apartmanı veya bağlamı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="f1591-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="f1591-111">Bu durum genellikle, grubun sahip olduğu tüm COM bileşenleri tamamen serbest bırakılmadan önce, bir RCW 'daki kullanıcı kodundan gelen açık çağrının veya CLR 'nin COM bileşenini (örneğin, ilişkili RCW 'ın çöp topladıktan sonra COM bileşeni serbest bırakıldığında) Bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f1591-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f1591-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f1591-112">Resolution</span></span>  
 <span data-ttu-id="f1591-113">Bu sorundan kaçınmak için, STA sahip olan iş parçacığının, uygulama, grupta bulunan tüm nesnelerle tamamlanmadan önce sonlandırılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1591-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="f1591-114">Aynı bağlamda geçerlidir; uygulamanın, bağlam içinde yaşayan herhangi bir COM bileşeni ile tamamen bitmeden önce bağlamların kapanmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1591-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f1591-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="f1591-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="f1591-116">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1591-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f1591-117">Yalnızca bağlantısı kesilen bağlamla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="f1591-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f1591-118">Çıktı</span><span class="sxs-lookup"><span data-stu-id="f1591-118">Output</span></span>  
 <span data-ttu-id="f1591-119">Bağlantısı kesilen grubun veya bağlamın bağlam tanımlama bilgisini raporlar.</span><span class="sxs-lookup"><span data-stu-id="f1591-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f1591-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1591-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1591-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1591-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f1591-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f1591-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f1591-123">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f1591-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
