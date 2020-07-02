---
title: overlappedFreeError MDA
description: .NET 'teki overlappedFreeError Managed hata ayıklama Yardımcısı 'nı (MDA) inceleyerek, erişim ihlallerinde veya atık toplanan yığının bozulmasıyla etkinleştirilebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 9be33c59723ecb2743f2bc610d7fb69d24ff388c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803929"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="cbd36-103">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="cbd36-103">overlappedFreeError MDA</span></span>
<span data-ttu-id="cbd36-104">`overlappedFreeError`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> yöntemi örtüşen işlem tamamlanmadan önce çağrıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cbd36-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cbd36-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="cbd36-105">Symptoms</span></span>  
 <span data-ttu-id="cbd36-106">Çöp toplanmış yığının erişim ihlalleri veya bozulması.</span><span class="sxs-lookup"><span data-stu-id="cbd36-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cbd36-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="cbd36-107">Cause</span></span>  
 <span data-ttu-id="cbd36-108">Çakışan bir yapı, işlem tamamlanmadan önce serbest bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cbd36-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="cbd36-109">Çakışan işaretçiyi kullanan işlev, daha sonra serbest olduktan sonra yapıya yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbd36-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="cbd36-110">Başka bir nesne artık bu bölgeyi kapladığı için yığın bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cbd36-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="cbd36-111">Çakışan işlem başarıyla başlamadıysanız Bu MDA bir hata temsil edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="cbd36-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cbd36-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="cbd36-112">Resolution</span></span>  
 <span data-ttu-id="cbd36-113">Metodu çağırmadan önce çakışan yapıyı kullanan g/ç işleminin tamamlandığından emin olun <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> .</span><span class="sxs-lookup"><span data-stu-id="cbd36-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cbd36-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="cbd36-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="cbd36-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cbd36-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cbd36-116">Çıktı</span><span class="sxs-lookup"><span data-stu-id="cbd36-116">Output</span></span>  
 <span data-ttu-id="cbd36-117">Bu MDA için örnek çıktı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cbd36-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="cbd36-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cbd36-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbd36-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd36-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="cbd36-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="cbd36-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cbd36-121">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="cbd36-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
