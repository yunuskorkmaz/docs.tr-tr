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
ms.workload: dotnet
ms.openlocfilehash: 33d1c7d91c33c194353af43deed9329b9b4ec841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="f44ae-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="f44ae-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="f44ae-103">`raceOnRCWCleanup` Ortak dil çalışma zamanı (CLR) algıladığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) gibibirkomutkullanarakbunuserbestbırakmakiçinbirçağrıyapılır,bunakullanın<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f44ae-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f44ae-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f44ae-104">Symptoms</span></span>  
 <span data-ttu-id="f44ae-105">Erişim ihlalleri veya Bellek Bozulması sırasında veya sonrasında kullanarak bir RCW boşaltma <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="f44ae-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f44ae-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="f44ae-106">Cause</span></span>  
 <span data-ttu-id="f44ae-107">RCW boşaltma iş parçacığı yığın veya başka bir iş parçacığı üzerinde kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="f44ae-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="f44ae-108">Kullanımda olan bir RCW bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f44ae-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f44ae-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f44ae-109">Resolution</span></span>  
 <span data-ttu-id="f44ae-110">Geçerli veya başka bir iş parçacığı kullanımda olabilir bir RCW boş değil.</span><span class="sxs-lookup"><span data-stu-id="f44ae-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f44ae-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="f44ae-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f44ae-112">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f44ae-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f44ae-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f44ae-113">Output</span></span>  
 <span data-ttu-id="f44ae-114">Hatayı açıklayan ileti.</span><span class="sxs-lookup"><span data-stu-id="f44ae-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f44ae-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f44ae-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f44ae-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f44ae-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f44ae-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f44ae-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f44ae-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f44ae-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
