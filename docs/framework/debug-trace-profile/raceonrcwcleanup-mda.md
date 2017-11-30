---
title: raceOnRCWCleanup MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 055ca5a85ca37401107b5cef8f6ff55237c3320b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="ccb42-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="ccb42-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="ccb42-103">`raceOnRCWCleanup` Ortak dil çalışma zamanı (CLR) algıladığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) gibibirkomutkullanarakbunuserbestbırakmakiçinbirçağrıyapılır,bunakullanın<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ccb42-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ccb42-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="ccb42-104">Symptoms</span></span>  
 <span data-ttu-id="ccb42-105">Erişim ihlalleri veya Bellek Bozulması sırasında veya sonrasında kullanarak bir RCW boşaltma <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="ccb42-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ccb42-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="ccb42-106">Cause</span></span>  
 <span data-ttu-id="ccb42-107">RCW boşaltma iş parçacığı yığın veya başka bir iş parçacığı üzerinde kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="ccb42-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="ccb42-108">Kullanımda olan bir RCW bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ccb42-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ccb42-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="ccb42-109">Resolution</span></span>  
 <span data-ttu-id="ccb42-110">Geçerli veya başka bir iş parçacığı kullanımda olabilir bir RCW boş değil.</span><span class="sxs-lookup"><span data-stu-id="ccb42-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ccb42-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="ccb42-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="ccb42-112">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccb42-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ccb42-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ccb42-113">Output</span></span>  
 <span data-ttu-id="ccb42-114">Hatayı açıklayan ileti.</span><span class="sxs-lookup"><span data-stu-id="ccb42-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ccb42-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ccb42-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccb42-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccb42-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="ccb42-117">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="ccb42-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="ccb42-118">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="ccb42-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
