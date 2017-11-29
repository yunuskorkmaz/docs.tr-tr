---
title: gcManagedToUnmanaged MDA
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
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aa528eb2acc872b1956edef3af3724bb3b54d67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="4bca1-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="4bca1-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="4bca1-103">`gcManagedToUnmanaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen kod için yönetilen bir iş parçacığı gelen geçiş her bir atık toplama neden olur.</span><span class="sxs-lookup"><span data-stu-id="4bca1-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4bca1-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4bca1-104">Symptoms</span></span>  
 <span data-ttu-id="4bca1-105">Bir yönetilmeyen kullanıcı bileşeni COM'a gösterilen yönetilen bir nesnenin kullanmaya çalışırken bir erişim ihlali oluşturur</span><span class="sxs-lookup"><span data-stu-id="4bca1-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="4bca1-106">COM nesnesi çıkarılan görünüyor.</span><span class="sxs-lookup"><span data-stu-id="4bca1-106">The COM object appears to have been released.</span></span> <span data-ttu-id="4bca1-107">Erişim ihlali belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="4bca1-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4bca1-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="4bca1-108">Cause</span></span>  
 <span data-ttu-id="4bca1-109">Yönetilmeyen bir bileşen başvuru yönetilen bir COM nesnesi düzgün sayım değilse, çalışma zamanı yönetilmeyen bileşen hala nesneye bir başvurusu tuttuğunda com'a yönetilen bir nesnenin toplamak.</span><span class="sxs-lookup"><span data-stu-id="4bca1-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="4bca1-110">Çalışma zamanı çağrıları <xref:System.Runtime.InteropServices.Marshal.Release%2A> çöp koleksiyonları sırasında şekilde çöp toplama oluşmadan önce kullanıcı Bileşen Nesne kullanıyorsa, sonra henüz alınamadı.</span><span class="sxs-lookup"><span data-stu-id="4bca1-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="4bca1-111">Bu nondeterminism kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="4bca1-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4bca1-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4bca1-112">Resolution</span></span>  
 <span data-ttu-id="4bca1-113">Bu Yardımcısı'nı etkinleştirme nesnesi için koleksiyonu uygun olduğunda arasında geçen zamanı azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> olarak adlandırılan, yönetilmeyen hangi bileşenin ilk toplanan nesne erişmeye çalıştığında aşağı izlemek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4bca1-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4bca1-114">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="4bca1-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="4bca1-115">Yönetilmeyen kod için bir iş parçacığı geçişler yönetilen her bir atık toplama neden olur.</span><span class="sxs-lookup"><span data-stu-id="4bca1-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4bca1-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="4bca1-116">Output</span></span>  
 <span data-ttu-id="4bca1-117">Bu MDA herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="4bca1-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4bca1-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4bca1-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bca1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bca1-119">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4bca1-120">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="4bca1-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4bca1-121">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="4bca1-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="4bca1-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="4bca1-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
