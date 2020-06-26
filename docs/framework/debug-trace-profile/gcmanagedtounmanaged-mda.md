---
title: gcManagedToUnmanaged MDA
description: GcManagedToUnmanaged Managed hata ayıklama Yardımcısı ' nı gözden geçirin. Bu MDA, yönetilmeyen koda geçiş sırasında zamanından önce çöp toplama işlemi nedeniyle etkinleştirilebilir.
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
ms.openlocfilehash: 76c621a1f2bb780d38228f2a84d4c77441774770
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415920"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="4fa6d-104">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="4fa6d-104">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="4fa6d-105">`gcManagedToUnmanaged`Yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-105">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4fa6d-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4fa6d-106">Symptoms</span></span>  
 <span data-ttu-id="4fa6d-107">Yönetilmeyen bir Kullanıcı bileşeni, COM 'a sunulan bir yönetilen nesneyi kullanmaya çalışırken bir erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-107">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="4fa6d-108">COM nesnesi yayımlanmış gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-108">The COM object appears to have been released.</span></span> <span data-ttu-id="4fa6d-109">Erişim ihlali belirleyici olmayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-109">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4fa6d-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="4fa6d-110">Cause</span></span>  
 <span data-ttu-id="4fa6d-111">Yönetilmeyen bir bileşen, yönetilen bir COM nesnesini doğru bir şekilde saymadığı takdirde, yönetilmeyen bileşen nesneye bir başvuru tuttuğunda, çalışma zamanı COM 'a sunulan bir yönetilen nesne toplayabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-111">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="4fa6d-112"><xref:System.Runtime.InteropServices.Marshal.Release%2A>Çöp koleksiyonları sırasında çalışma zamanı çağırır, bu nedenle Kullanıcı bileşeni atık toplama gerçekleşmeden önce nesneyi kullanıyorsa, henüz toplanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-112">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="4fa6d-113">Bu, belirleyici olmayan bir ISM kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-113">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4fa6d-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4fa6d-114">Resolution</span></span>  
 <span data-ttu-id="4fa6d-115">Bu yardımcıyı etkinleştirmek, nesnenin koleksiyon için uygun olduğu zaman arasındaki süreyi azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> çağrılır, hangi yönetilmeyen bileşenin ilk olarak toplanan nesneye erişmeye çalıştığını izlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-115">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4fa6d-116">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4fa6d-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="4fa6d-117">Her iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-117">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4fa6d-118">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4fa6d-118">Output</span></span>  
 <span data-ttu-id="4fa6d-119">Bu MDA hiçbir çıkış üretmez.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-119">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4fa6d-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4fa6d-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fa6d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa6d-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4fa6d-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4fa6d-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4fa6d-123">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4fa6d-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="4fa6d-124">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="4fa6d-124">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
