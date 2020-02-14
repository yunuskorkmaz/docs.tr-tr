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
ms.openlocfilehash: 1f557cc370d5c6121b0ad9a4528bd75dcb70a93c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216284"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="1ddf8-102">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="1ddf8-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="1ddf8-103">`invalidOverlappedToPinvoke` yönetilen hata ayıklama Yardımcısı (MDA), çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ddf8-104">Varsayılan olarak, bu MDA yalnızca platform çağırma çağrısı kodunuzda tanımlanmışsa ve hata ayıklayıcı her yöntemin Adamcode durumunu bildirirse etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="1ddf8-105">Bir hata ayıklayıcı (örneğin, hiçbir uzantısı olmayan MDbg. exe) Bu MDA ' i etkinleştirmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="1ddf8-106">Bu MDA, bir yapılandırma dosyası kullanılarak bu hata ayıklayıcılar için etkinleştirilebilir ve. mda. config dosyasında `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`) açıkça `justMyCode="false"`.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1ddf8-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1ddf8-107">Symptoms</span></span>  
 <span data-ttu-id="1ddf8-108">Kilitlenmeler veya unexplainable yığın bozulmaları.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1ddf8-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="1ddf8-109">Cause</span></span>  
 <span data-ttu-id="1ddf8-110">Çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="1ddf8-111">Aşağıdaki tabloda bu MDA 'ın izlediği işlevler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="1ddf8-112">Modül</span><span class="sxs-lookup"><span data-stu-id="1ddf8-112">Module</span></span>|<span data-ttu-id="1ddf8-113">İşlev</span><span class="sxs-lookup"><span data-stu-id="1ddf8-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="1ddf8-114">HTTPAPI. dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="1ddf8-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="1ddf8-116">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="1ddf8-117">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="1ddf8-118">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="1ddf8-119">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="1ddf8-120">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="1ddf8-121">paketindeki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="1ddf8-122">MSWSock. dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="1ddf8-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="1ddf8-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="1ddf8-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="1ddf8-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="1ddf8-127">MQRT. dll</span><span class="sxs-lookup"><span data-stu-id="1ddf8-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="1ddf8-128">Çağrıyı yapan <xref:System.AppDomain>, bu durum için yığın bozulması olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="1ddf8-129"><xref:System.AppDomain> kaldırılırsa, uygulama kodu çakışan işaretçi için belleği serbest kalacak, işlem bittiğinde bozulmaya neden olur veya kod belleği sızdırdığınızda, daha sonra zorluklara neden olur.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1ddf8-130">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1ddf8-130">Resolution</span></span>  
 <span data-ttu-id="1ddf8-131">İşleve geçirilebilecek <xref:System.Threading.NativeOverlapped> yapısını almak için <xref:System.Threading.Overlapped.Pack%2A> metodunu çağırarak bir <xref:System.Threading.Overlapped> nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="1ddf8-132"><xref:System.AppDomain> kaldırıldığında CLR, işaretçiyi boşaltmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1ddf8-133">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="1ddf8-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="1ddf8-134">Bu MDA, CLR üzerinde hiçbir etkisi yoktu.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1ddf8-135">Çıktı</span><span class="sxs-lookup"><span data-stu-id="1ddf8-135">Output</span></span>  
 <span data-ttu-id="1ddf8-136">Aşağıda, bu MDA 'ın çıkış örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="1ddf8-137">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1ddf8-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ddf8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ddf8-138">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1ddf8-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1ddf8-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1ddf8-140">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1ddf8-140">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
