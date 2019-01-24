---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: add5ba59f8f59fc013f8c04a186b34e711c1490c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537939"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="7103c-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="7103c-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="7103c-103">`gcManagedToUnmanaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen kod için yönetilen bir iş parçacığı gelen geçiş her bir çöp toplamanın neden olur.</span><span class="sxs-lookup"><span data-stu-id="7103c-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7103c-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7103c-104">Symptoms</span></span>  
 <span data-ttu-id="7103c-105">Yönetilmeyen kullanıcı bileşeni COM tarafından sunulan bir yönetilen nesne kullanmaya çalışırken bir erişim ihlali oluşturur</span><span class="sxs-lookup"><span data-stu-id="7103c-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="7103c-106">COM nesnesi yayımlanan görünüyor.</span><span class="sxs-lookup"><span data-stu-id="7103c-106">The COM object appears to have been released.</span></span> <span data-ttu-id="7103c-107">Erişim ihlali belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="7103c-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7103c-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="7103c-108">Cause</span></span>  
 <span data-ttu-id="7103c-109">Yönetilmeyen bir bileşene başvuru yönetilen bir COM nesnesi düzgün sayımı değilse, çalışma zamanının yönetilen bir nesnenin yönetilmeyen bileşeni hala nesnesine bir başvuru tuttuğunda com'a toplamanız mümkündü.</span><span class="sxs-lookup"><span data-stu-id="7103c-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="7103c-110">Çalışma zamanı çağrıları <xref:System.Runtime.InteropServices.Marshal.Release%2A> atık toplama sırasında kadar çöp toplama oluşmadan önce nesne kullanıcı bileşen kullanıyorsa, ardından bunu değil henüz toplanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="7103c-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="7103c-111">Bu nondeterminism kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="7103c-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7103c-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7103c-112">Resolution</span></span>  
 <span data-ttu-id="7103c-113">Bu Yardımcısı'nı etkinleştirme, nesne koleksiyonu için uygun olduğunda arasındaki süreyi azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> olarak adlandırılan, hangi yönetilmeyen bileşen önce toplanan nesneye erişme girişiminde aşağı izlemek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7103c-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7103c-114">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="7103c-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="7103c-115">Bir iş parçacığı geçişler yönetilmeyen kod için yönetilen her bir çöp toplamanın neden olur.</span><span class="sxs-lookup"><span data-stu-id="7103c-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7103c-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="7103c-116">Output</span></span>  
 <span data-ttu-id="7103c-117">Bu mda'nın herhangi bir çıktı üretmez.</span><span class="sxs-lookup"><span data-stu-id="7103c-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7103c-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7103c-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7103c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7103c-119">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7103c-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7103c-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7103c-121">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7103c-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="7103c-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="7103c-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
