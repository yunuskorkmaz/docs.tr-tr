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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6400986d58fcb5f11d06e371a1b58f5256f4c62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629372"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="a7fbe-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="a7fbe-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="a7fbe-103">Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir çalışma zamanında çağrılabilir sarmalayıcı (RCW) kullanımda olduğunu algıladığında etkinleştirilir. `raceOnRCWCleanup`</span><span class="sxs-lookup"><span data-stu-id="a7fbe-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a7fbe-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a7fbe-104">Symptoms</span></span>  
 <span data-ttu-id="a7fbe-105">Ya da benzer bir yöntemi kullanarak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a7fbe-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="a7fbe-106">Cause</span></span>  
 <span data-ttu-id="a7fbe-107">RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="a7fbe-108">Kullanımda olan bir RCW yayımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a7fbe-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a7fbe-109">Resolution</span></span>  
 <span data-ttu-id="a7fbe-110">Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a7fbe-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="a7fbe-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="a7fbe-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a7fbe-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a7fbe-113">Output</span></span>  
 <span data-ttu-id="a7fbe-114">Hatayı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a7fbe-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7fbe-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7fbe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7fbe-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a7fbe-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a7fbe-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a7fbe-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a7fbe-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
