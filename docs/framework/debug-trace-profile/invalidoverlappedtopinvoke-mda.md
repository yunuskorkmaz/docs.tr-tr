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
ms.openlocfilehash: 4bdb2035906b9383342201017b58d1d0050113b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084563"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="adb36-102">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="adb36-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="adb36-103">`invalidOverlappedToPinvoke` Yönetilen hata ayıklama Yardımcısı (MDA) çöp koleksiyonu yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="adb36-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adb36-104">Varsayılan olarak, bu MDA, yalnızca platform çağırma çağrısı kodunuzda tanımlanır ve hata ayıklayıcı her yöntemin JustMyCode durumunu raporlar etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="adb36-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="adb36-105">JustMyCode (örneğin, MDbg.exe uzantısız) anlamıyor bir hata ayıklayıcı bu mda'nın etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="adb36-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="adb36-106">Bu MDA etkinleştirilebilir bu hata ayıklayıcıları için bir yapılandırma dosyası ve açıkça mda.config kullanarak `justMyCode="false"` içinde. mda.config dosyasından `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="adb36-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="adb36-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="adb36-107">Symptoms</span></span>  
 <span data-ttu-id="adb36-108">Sistem çökmeleri ya da açıklanamaz yığın bozulmaları.</span><span class="sxs-lookup"><span data-stu-id="adb36-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="adb36-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="adb36-109">Cause</span></span>  
 <span data-ttu-id="adb36-110">Çöp koleksiyonu yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="adb36-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="adb36-111">Aşağıdaki tablo bu mda'nın izlediği işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="adb36-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="adb36-112">Modül</span><span class="sxs-lookup"><span data-stu-id="adb36-112">Module</span></span>|<span data-ttu-id="adb36-113">İşlev</span><span class="sxs-lookup"><span data-stu-id="adb36-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="adb36-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="adb36-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="adb36-116">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="adb36-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="adb36-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="adb36-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="adb36-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="adb36-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="adb36-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="adb36-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="adb36-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="adb36-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="adb36-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="adb36-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="adb36-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="adb36-128">Çünkü bu koşul için yığın bozulma olasılığı yüksektir <xref:System.AppDomain> yapılıyor çağrısını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="adb36-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="adb36-129">Varsa <xref:System.AppDomain> kaldırılırsa, uygulama kodu serbest bırakacak ya da işlem bittiğinde ya da kod bellekte sızıntı oluşturacaktır Bozulması neden, daha sonra sorunlarla neden Çakışan işaretçi için bellek.</span><span class="sxs-lookup"><span data-stu-id="adb36-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="adb36-130">Çözüm</span><span class="sxs-lookup"><span data-stu-id="adb36-130">Resolution</span></span>  
 <span data-ttu-id="adb36-131">Kullanım bir <xref:System.Threading.Overlapped> çağrılırken, nesne <xref:System.Threading.Overlapped.Pack%2A> almak için yöntemi bir <xref:System.Threading.NativeOverlapped> işleve geçirilen yapısı.</span><span class="sxs-lookup"><span data-stu-id="adb36-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="adb36-132">Varsa <xref:System.AppDomain> kaldırılırsa CLR işaretçi serbest bırakılmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="adb36-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="adb36-133">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="adb36-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="adb36-134">Bu mda'nın CLR üzerinde hiçbir etkisi vardı.</span><span class="sxs-lookup"><span data-stu-id="adb36-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="adb36-135">Çıkış</span><span class="sxs-lookup"><span data-stu-id="adb36-135">Output</span></span>  
 <span data-ttu-id="adb36-136">Bu mda'nın bir örnek çıktı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="adb36-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="adb36-137">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adb36-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adb36-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adb36-138">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="adb36-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="adb36-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="adb36-140">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="adb36-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
