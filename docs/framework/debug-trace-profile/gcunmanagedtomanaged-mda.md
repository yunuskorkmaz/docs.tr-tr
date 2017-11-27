---
title: gcUnmanagedToManaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e8d2391ba9ba1d17f2cbce54f52863f74a5dc646
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="7257a-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="7257a-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="7257a-103">`gcUnmanagedToManaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen koddan yönetilen koda gelen bir iş parçacığı geçişleri her bir atık toplama neden olur.</span><span class="sxs-lookup"><span data-stu-id="7257a-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7257a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7257a-104">Symptoms</span></span>  
 <span data-ttu-id="7257a-105">COM ve platform kullanarak çalışan yönetilmeyen kullanıcı bileşenleri çağırma uygulama CLR belirleyici olmayan erişim ihlali neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="7257a-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7257a-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="7257a-106">Cause</span></span>  
 <span data-ttu-id="7257a-107">Ardından uygulamanın yönetilmeyen kullanıcı bileşenleri çalışıyorsa, bu bileşenlerin çöpünün toplanma yığın bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="7257a-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="7257a-108">Çöp toplayıcı nesnesi grafik yol denediğinde bu CLR bir erişim ihlali neden olur.</span><span class="sxs-lookup"><span data-stu-id="7257a-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7257a-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7257a-109">Resolution</span></span>  
 <span data-ttu-id="7257a-110">Bu yardımcı etkinleştirme ne zaman yönetilmeyen bileşen çöpünün toplanma yığın bozarsa ve erişim ihlali her yönetilen geçiş önce gerçekleşmesi için bir atık toplama zorlayarak durumda arasındaki süreyi azaltır.</span><span class="sxs-lookup"><span data-stu-id="7257a-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7257a-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="7257a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="7257a-112">İş parçacığı geçişleri yönetilmeyenden yönetilen kodu her bir atık toplama neden olur.</span><span class="sxs-lookup"><span data-stu-id="7257a-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7257a-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="7257a-113">Output</span></span>  
 <span data-ttu-id="7257a-114">Bu MDA herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="7257a-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7257a-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7257a-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7257a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7257a-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7257a-117">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="7257a-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7257a-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="7257a-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [<span data-ttu-id="7257a-119">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="7257a-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
