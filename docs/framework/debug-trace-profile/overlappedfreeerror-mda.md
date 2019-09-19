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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70d31bc187cabe49351e86a20023e2ec65e87b94
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052396"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="250e2-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="250e2-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="250e2-103">Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi örtüşen işlem tamamlanmadan önce çağrıldığında etkinleştirilir. `overlappedFreeError`</span><span class="sxs-lookup"><span data-stu-id="250e2-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="250e2-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="250e2-104">Symptoms</span></span>  
 <span data-ttu-id="250e2-105">Çöp toplanmış yığının erişim ihlalleri veya bozulması.</span><span class="sxs-lookup"><span data-stu-id="250e2-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="250e2-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="250e2-106">Cause</span></span>  
 <span data-ttu-id="250e2-107">Çakışan bir yapı, işlem tamamlanmadan önce serbest bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="250e2-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="250e2-108">Çakışan işaretçiyi kullanan işlev, daha sonra serbest olduktan sonra yapıya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="250e2-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="250e2-109">Başka bir nesne artık bu bölgeyi kapladığı için yığın bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="250e2-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="250e2-110">Çakışan işlem başarıyla başlamadıysanız Bu MDA bir hata temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="250e2-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="250e2-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="250e2-111">Resolution</span></span>  
 <span data-ttu-id="250e2-112"><xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> Metodu çağırmadan önce çakışan yapıyı kullanan g/ç işleminin tamamlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="250e2-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="250e2-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="250e2-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="250e2-114">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="250e2-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="250e2-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="250e2-115">Output</span></span>  
 <span data-ttu-id="250e2-116">Bu MDA için örnek çıktı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="250e2-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="250e2-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="250e2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="250e2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="250e2-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="250e2-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="250e2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="250e2-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="250e2-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
