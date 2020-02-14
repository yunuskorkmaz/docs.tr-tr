---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216191"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="5c917-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="5c917-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="5c917-103">`raceOnRCWCleanup` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir çalışma zamanı çağrılabilir sarmalayıcı (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) kullanımda olduğunu algıladığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5c917-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5c917-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="5c917-104">Symptoms</span></span>  
 <span data-ttu-id="5c917-105"><xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem kullanarak bir RCW boşaltılırken veya sonrasında ihlal veya bellek bozulmasına erişin.</span><span class="sxs-lookup"><span data-stu-id="5c917-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5c917-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="5c917-106">Cause</span></span>  
 <span data-ttu-id="5c917-107">RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="5c917-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="5c917-108">Kullanımda olan bir RCW yayımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="5c917-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5c917-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="5c917-109">Resolution</span></span>  
 <span data-ttu-id="5c917-110">Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.</span><span class="sxs-lookup"><span data-stu-id="5c917-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5c917-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="5c917-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="5c917-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c917-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5c917-113">Çıktı</span><span class="sxs-lookup"><span data-stu-id="5c917-113">Output</span></span>  
 <span data-ttu-id="5c917-114">Hatayı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="5c917-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5c917-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5c917-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c917-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c917-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5c917-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="5c917-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5c917-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="5c917-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
