---
title: gcUnmanagedToManaged MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f662114868832f909d734a482e1dc9aefb841a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150886"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="11e9a-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="11e9a-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="11e9a-103">`gcUnmanagedToManaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilen kodu için yönetilmeyen bir iş parçacığı gelen geçiş her bir çöp toplamanın neden olur.</span><span class="sxs-lookup"><span data-stu-id="11e9a-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="11e9a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="11e9a-104">Symptoms</span></span>  
 <span data-ttu-id="11e9a-105">COM ve platformu kullanarak çalışan yönetilmeyen kullanıcı bileşenleri çağırma uygulama CLR'de belirleyici olmayan erişim ihlaline neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="11e9a-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="11e9a-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="11e9a-106">Cause</span></span>  
 <span data-ttu-id="11e9a-107">Ardından uygulamanın yönetilmeyen kullanıcı bileşenleri çalışıyorsa, bu bileşenlerin atık olarak toplanmış yığınla bozulmuş.</span><span class="sxs-lookup"><span data-stu-id="11e9a-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="11e9a-108">Atık toplayıcı Nesne grafiğini yol denediğinde bu CLR'de erişim ihlaline neden olur.</span><span class="sxs-lookup"><span data-stu-id="11e9a-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="11e9a-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="11e9a-109">Resolution</span></span>  
 <span data-ttu-id="11e9a-110">Bu Yardımcısı'nı etkinleştirme, yönetilmeyen bileşeni atık olarak toplanmış yığınla bozarsa ve bir çöp toplama, yönetilen her geçiş önce gerçekleşmesi için zorlayarak erişim ihlali durumda arasındaki süreyi azaltır.</span><span class="sxs-lookup"><span data-stu-id="11e9a-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="11e9a-111">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="11e9a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="11e9a-112">Yönetilen kod için yönetilmeyen bir iş parçacığı geçişler her bir çöp toplamanın neden olur.</span><span class="sxs-lookup"><span data-stu-id="11e9a-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="11e9a-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="11e9a-113">Output</span></span>  
 <span data-ttu-id="11e9a-114">Bu mda'nın herhangi bir çıktı üretmez.</span><span class="sxs-lookup"><span data-stu-id="11e9a-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="11e9a-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="11e9a-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11e9a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11e9a-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="11e9a-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="11e9a-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="11e9a-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="11e9a-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="11e9a-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="11e9a-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
