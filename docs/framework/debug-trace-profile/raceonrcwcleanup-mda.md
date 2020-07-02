---
title: raceOnRCWCleanup MDA
description: RCW başka bir iş parçacığında veya .NET 'teki iş parçacığı yığınında kullanılıyorsa etkinleştirilen Esrcwcleanup yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803657"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="6f778-103">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="6f778-103">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="6f778-104">`raceOnRCWCleanup`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir çalışma zamanı çağrılabilir sarmalayıcı (RCW), yöntemi gibi bir komut kullanılarak yapıldığında bir [çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) kullanımda olduğunu algıladığında etkinleştirilir <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f778-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6f778-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="6f778-105">Symptoms</span></span>  
 <span data-ttu-id="6f778-106">Ya da benzer bir yöntemi kullanarak bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f778-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6f778-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="6f778-107">Cause</span></span>  
 <span data-ttu-id="6f778-108">RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="6f778-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="6f778-109">Kullanımda olan bir RCW yayımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="6f778-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6f778-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6f778-110">Resolution</span></span>  
 <span data-ttu-id="6f778-111">Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.</span><span class="sxs-lookup"><span data-stu-id="6f778-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6f778-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="6f778-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="6f778-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f778-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6f778-114">Çıktı</span><span class="sxs-lookup"><span data-stu-id="6f778-114">Output</span></span>  
 <span data-ttu-id="6f778-115">Hatayı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="6f778-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6f778-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f778-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f778-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f778-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6f778-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="6f778-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6f778-119">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="6f778-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
