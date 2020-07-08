---
title: invalidOverlappedToPinvoke MDA
description: .NET 'teki invalidOverlappedToPinvoke Managed hata ayıklama Yardımcısı 'nı (MDA), kilitlenme veya bir unexplainable yığın bozulması sırasında etkinleştirilebilecek şekilde gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051707"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="33f37-103">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="33f37-103">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="33f37-104">`invalidOverlappedToPinvoke`Yönetilen hata ayıklama Yardımcısı (MDA), çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli Win32 işlevlerine geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33f37-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33f37-105">Varsayılan olarak, bu MDA yalnızca platform çağırma çağrısı kodunuzda tanımlanmışsa ve hata ayıklayıcı her yöntemin Adamcode durumunu bildirirse etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33f37-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="33f37-106">Bir hata ayıklayıcı (uzantısı olmayan MDbg.exe gibi), bu MDA ' i etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="33f37-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="33f37-107">Bu MDA, bu hata ayıklayıcılar için bir yapılandırma dosyası kullanılarak ve .mda.config dosyasında açıkça bir şekilde çalıştırılarak etkinleştirilebilir `justMyCode="false"` `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>` .</span><span class="sxs-lookup"><span data-stu-id="33f37-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="33f37-108">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="33f37-108">Symptoms</span></span>  
 <span data-ttu-id="33f37-109">Kilitlenmeler veya unexplainable yığın bozulmaları.</span><span class="sxs-lookup"><span data-stu-id="33f37-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="33f37-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="33f37-110">Cause</span></span>  
 <span data-ttu-id="33f37-111">Çöp toplama yığınında oluşturulmamış bir çakışan işaretçi belirli işletim sistemi işlevlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="33f37-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="33f37-112">Aşağıdaki tabloda bu MDA 'ın izlediği işlevler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33f37-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="33f37-113">Modül</span><span class="sxs-lookup"><span data-stu-id="33f37-113">Module</span></span>|<span data-ttu-id="33f37-114">İşlev</span><span class="sxs-lookup"><span data-stu-id="33f37-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="33f37-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="33f37-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="33f37-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="33f37-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="33f37-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="33f37-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="33f37-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="33f37-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="33f37-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="33f37-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="33f37-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="33f37-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="33f37-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="33f37-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="33f37-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="33f37-129">Bu durum için yığın bozulması olasılığı yüksektir çünkü çağrının kaldırılması mümkün olur <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="33f37-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="33f37-130">Kaldırılırsa <xref:System.AppDomain> , uygulama kodu çakışan işaretçi için belleği serbest kalacak, işlem bittiğinde bozulmaya neden olur veya kod belleği sızıntısına neden olur ve daha sonra zorluklara yol açar.</span><span class="sxs-lookup"><span data-stu-id="33f37-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="33f37-131">Çözüm</span><span class="sxs-lookup"><span data-stu-id="33f37-131">Resolution</span></span>  
 <span data-ttu-id="33f37-132"><xref:System.Threading.Overlapped> <xref:System.Threading.Overlapped.Pack%2A> İşleve geçirilebilecek bir yapı almak için yöntemini çağırarak bir nesnesi kullanın <xref:System.Threading.NativeOverlapped> .</span><span class="sxs-lookup"><span data-stu-id="33f37-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="33f37-133"><xref:System.AppDomain>Kaldırıldığında, clr, işaretçiyi boşaltmadan önce zaman uyumsuz işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="33f37-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="33f37-134">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="33f37-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="33f37-135">Bu MDA, CLR üzerinde hiçbir etkisi yoktu.</span><span class="sxs-lookup"><span data-stu-id="33f37-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="33f37-136">Çıktı</span><span class="sxs-lookup"><span data-stu-id="33f37-136">Output</span></span>  
 <span data-ttu-id="33f37-137">Aşağıda, bu MDA 'ın çıkış örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33f37-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="33f37-138">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33f37-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33f37-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33f37-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="33f37-140">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="33f37-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="33f37-141">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="33f37-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
