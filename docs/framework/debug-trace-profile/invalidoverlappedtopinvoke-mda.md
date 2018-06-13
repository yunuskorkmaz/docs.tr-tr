---
title: invalidOverlappedToPinvoke MDA
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7240692e35c97f3efbc33ca27a0221da1d250149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386863"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="6f110-102">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="6f110-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="6f110-103">`invalidOverlappedToPinvoke` Yönetilen hata ayıklama Yardımcısı (MDA) atık toplama yığında oluşturulmayan Çakışan işaretçi belirli Win32 işlevleri geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6f110-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f110-104">Varsayılan olarak, bu MDA platform çağırma çağrısı kodunuzda tanımlanır ve hata ayıklayıcısı her yöntemi JustMyCode durumunu raporlar yalnızca etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6f110-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="6f110-105">(Örneğin, MDbg.exe uzantısız) JustMyCode anlamıyor bir hata ayıklayıcısı bu MDA etkinleştirmemek.</span><span class="sxs-lookup"><span data-stu-id="6f110-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="6f110-106">Bu MDA etkinleştirilebilir bu hata ayıklayıcıları için bir yapılandırma dosyası ve açıkça ayarlarını kullanarak `justMyCode="false"` içinde. mda.config dosya `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="6f110-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6f110-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="6f110-107">Symptoms</span></span>  
 <span data-ttu-id="6f110-108">Kilitlenme veya unexplainable yığın bozulmaları.</span><span class="sxs-lookup"><span data-stu-id="6f110-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6f110-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="6f110-109">Cause</span></span>  
 <span data-ttu-id="6f110-110">Çöp toplama yığında oluşturulmayan Çakışan işaretçi belirli işletim sistemi işlevleri geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6f110-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="6f110-111">Aşağıdaki tabloda, bu MDA izleyen işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f110-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="6f110-112">Modül</span><span class="sxs-lookup"><span data-stu-id="6f110-112">Module</span></span>|<span data-ttu-id="6f110-113">İşlev</span><span class="sxs-lookup"><span data-stu-id="6f110-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="6f110-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="6f110-115">Iphlpapi.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="6f110-116">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="6f110-117">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="6f110-118">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="6f110-119">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="6f110-120">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="6f110-121">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="6f110-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="6f110-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="6f110-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="6f110-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="6f110-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="6f110-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="6f110-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="6f110-128">Bu koşul için olduğundan olası yığın bozulması yüksek <xref:System.AppDomain> çağrı unload yapma.</span><span class="sxs-lookup"><span data-stu-id="6f110-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="6f110-129">Varsa <xref:System.AppDomain> kaldırır, uygulama kodu ya da ücretsiz işlemi bittikten ya da kod bellek sızıntısı Bozulması neden, daha sonra sorunlarla neden Çakışan işaretçi için bellek.</span><span class="sxs-lookup"><span data-stu-id="6f110-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6f110-130">Çözüm</span><span class="sxs-lookup"><span data-stu-id="6f110-130">Resolution</span></span>  
 <span data-ttu-id="6f110-131">Kullanım bir <xref:System.Threading.Overlapped> çağrılırken, nesne <xref:System.Threading.Overlapped.Pack%2A> almak için yöntemi bir <xref:System.Threading.NativeOverlapped> işlevine geçirilen yapısı.</span><span class="sxs-lookup"><span data-stu-id="6f110-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="6f110-132">Varsa <xref:System.AppDomain> kaldırır, CLR bekler işaretçinin boşaltma önce zaman uyumsuz işlemi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="6f110-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6f110-133">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="6f110-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="6f110-134">Bu MDA CLR üzerinde hiçbir etkisi vardı.</span><span class="sxs-lookup"><span data-stu-id="6f110-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6f110-135">Çıkış</span><span class="sxs-lookup"><span data-stu-id="6f110-135">Output</span></span>  
 <span data-ttu-id="6f110-136">Bu MDA çıktının bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f110-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="6f110-137">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f110-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f110-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f110-138">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="6f110-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="6f110-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="6f110-140">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="6f110-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
