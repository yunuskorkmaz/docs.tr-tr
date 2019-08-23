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
ms.openlocfilehash: ca3b28d0d27af0a752de894f5856b76939b01e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967248"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="a7398-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="a7398-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="a7398-103">Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir çalışma zamanında çağrılabilir sarmalayıcı (RCW) kullanımda olduğunu algıladığında etkinleştirilir. `raceOnRCWCleanup`</span><span class="sxs-lookup"><span data-stu-id="a7398-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a7398-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a7398-104">Symptoms</span></span>  
 <span data-ttu-id="a7398-105">Ya da benzer bir yöntemi kullanarak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin.</span><span class="sxs-lookup"><span data-stu-id="a7398-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a7398-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="a7398-106">Cause</span></span>  
 <span data-ttu-id="a7398-107">RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a7398-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="a7398-108">Kullanımda olan bir RCW yayımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a7398-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a7398-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a7398-109">Resolution</span></span>  
 <span data-ttu-id="a7398-110">Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.</span><span class="sxs-lookup"><span data-stu-id="a7398-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a7398-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="a7398-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="a7398-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7398-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a7398-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a7398-113">Output</span></span>  
 <span data-ttu-id="a7398-114">Hatayı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="a7398-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a7398-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7398-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7398-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7398-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a7398-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a7398-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a7398-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a7398-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
