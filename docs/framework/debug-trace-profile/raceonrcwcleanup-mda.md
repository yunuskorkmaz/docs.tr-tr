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
ms.openlocfilehash: 393c5ea44108445a9a1a9d16e7d1d192eced5740
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271453"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="c655c-103">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="c655c-103">raceOnRCWCleanup MDA</span></span>

<span data-ttu-id="c655c-104">`raceOnRCWCleanup`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir çalışma zamanı çağrılabilir sarmalayıcı (RCW), yöntemi gibi bir komut kullanılarak yapıldığında bir [çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) kullanımda olduğunu algıladığında etkinleştirilir <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c655c-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c655c-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c655c-105">Symptoms</span></span>  

 <span data-ttu-id="c655c-106">Ya da benzer bir yöntemi kullanarak bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="c655c-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c655c-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="c655c-107">Cause</span></span>  

 <span data-ttu-id="c655c-108">RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="c655c-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="c655c-109">Kullanımda olan bir RCW yayımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c655c-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c655c-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c655c-110">Resolution</span></span>  

 <span data-ttu-id="c655c-111">Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.</span><span class="sxs-lookup"><span data-stu-id="c655c-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c655c-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c655c-112">Effect on the Runtime</span></span>  

 <span data-ttu-id="c655c-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c655c-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c655c-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c655c-114">Output</span></span>  

 <span data-ttu-id="c655c-115">Hatayı açıklayan bir ileti.</span><span class="sxs-lookup"><span data-stu-id="c655c-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c655c-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c655c-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c655c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c655c-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c655c-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c655c-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c655c-119">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c655c-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
