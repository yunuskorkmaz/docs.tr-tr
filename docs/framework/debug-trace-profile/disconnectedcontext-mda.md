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
ms.openlocfilehash: 5d97ee808ef7d2a14902259c47227b787f0830fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629386"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="823a9-102">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="823a9-102">disconnectedContext MDA</span></span>
<span data-ttu-id="823a9-103">`disconnectedContext` Yönetilen hata ayıklama Yardımcısı (MDA), clr bir com nesnesiyle ilgili bir isteğe hizmet verirken, bağlantısı kesilen bir gruba veya içeriğe geçişe çalıştığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="823a9-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="823a9-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="823a9-104">Symptoms</span></span>  
 <span data-ttu-id="823a9-105">[Çalışma zamanında çağrılabilir sarmalayıcı](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde yapılan çağrılar, mevcut grubun veya bağlamdaki temel alınan com bileşenine sahip oldukları bir yerine, geçerli grupta veya bağlamda dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="823a9-105">Calls made on a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="823a9-106">Bu, tek iş parçacıklı apartman (STA) bileşenlerinde olduğu gibi COM bileşeni çok iş parçacıklı değilse bozulma ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="823a9-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="823a9-107">Alternatif olarak, RCW kendisi bir ara sunucu ise, çağrı bir <xref:System.Runtime.InteropServices.COMException> HRESULT RPC_E_WRONG_THREAD ile birlikte Oluşturuma yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="823a9-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="823a9-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="823a9-108">Cause</span></span>  
 <span data-ttu-id="823a9-109">CLR kendisine geçişe çalıştığında OLE Apartmanı veya bağlamı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="823a9-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="823a9-110">Bu en yaygın olarak, grubun sahip olduğu tüm COM bileşenleri tamamen serbest bırakılmadan, bu durum genellikle, bir RCW 'daki kullanıcı kodundan gelen açık çağrının veya CLR 'nin COM bileşenini düzenleme yaptığı sırada gerçekleşebilir. Örneğin, CLR, ilişkili RCW atık olarak toplandığında COM bileşeni serbest bırakıldığında.</span><span class="sxs-lookup"><span data-stu-id="823a9-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="823a9-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="823a9-111">Resolution</span></span>  
 <span data-ttu-id="823a9-112">Bu sorundan kaçınmak için, STA sahip olan iş parçacığının, uygulama, grupta bulunan tüm nesnelerle tamamlanmadan önce sonlandırılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="823a9-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="823a9-113">Aynı bağlamda geçerlidir; uygulamanın, bağlam içinde yaşayan herhangi bir COM bileşeni ile tamamen bitmeden önce bağlamların kapanmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="823a9-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="823a9-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="823a9-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="823a9-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="823a9-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="823a9-116">Yalnızca bağlantısı kesilen bağlamla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="823a9-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="823a9-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="823a9-117">Output</span></span>  
 <span data-ttu-id="823a9-118">Bağlantısı kesilen grubun veya bağlamın bağlam tanımlama bilgisini raporlar.</span><span class="sxs-lookup"><span data-stu-id="823a9-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="823a9-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="823a9-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="823a9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="823a9-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="823a9-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="823a9-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="823a9-122">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="823a9-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
