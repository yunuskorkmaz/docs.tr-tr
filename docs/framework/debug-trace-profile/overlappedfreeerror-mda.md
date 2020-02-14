---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 8a0c72cf26ef8434719ff6661ef15a44f51c8740
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217259"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="1c8f6-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="1c8f6-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="1c8f6-103">`overlappedFreeError` yönetilen hata ayıklama Yardımcısı (MDA), çakışan işlem tamamlanmadan önce <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi çağrıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1c8f6-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1c8f6-104">Symptoms</span></span>  
 <span data-ttu-id="1c8f6-105">Çöp toplanmış yığının erişim ihlalleri veya bozulması.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1c8f6-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="1c8f6-106">Cause</span></span>  
 <span data-ttu-id="1c8f6-107">Çakışan bir yapı, işlem tamamlanmadan önce serbest bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="1c8f6-108">Çakışan işaretçiyi kullanan işlev, daha sonra serbest olduktan sonra yapıya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="1c8f6-109">Başka bir nesne artık bu bölgeyi kapladığı için yığın bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="1c8f6-110">Çakışan işlem başarıyla başlamadıysanız Bu MDA bir hata temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1c8f6-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1c8f6-111">Resolution</span></span>  
 <span data-ttu-id="1c8f6-112"><xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> yöntemi çağrılmadan önce çakışan yapıyı kullanan g/ç işleminin tamamlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1c8f6-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="1c8f6-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="1c8f6-114">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1c8f6-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="1c8f6-115">Output</span></span>  
 <span data-ttu-id="1c8f6-116">Bu MDA için örnek çıktı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="1c8f6-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1c8f6-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c8f6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8f6-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1c8f6-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1c8f6-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1c8f6-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1c8f6-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
