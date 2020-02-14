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
ms.openlocfilehash: f7e6334e20a6e0db1d52307a833de0ecd0d74cc4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217485"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="c1538-102">gcManagedToUnmanaged MDA</span><span class="sxs-lookup"><span data-stu-id="c1538-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="c1538-103">`gcManagedToUnmanaged` yönetilen hata ayıklama Yardımcısı (MDA), her bir iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c1538-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c1538-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c1538-104">Symptoms</span></span>  
 <span data-ttu-id="c1538-105">Yönetilmeyen bir Kullanıcı bileşeni, COM 'a sunulan bir yönetilen nesneyi kullanmaya çalışırken bir erişim ihlali oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1538-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="c1538-106">COM nesnesi yayımlanmış gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="c1538-106">The COM object appears to have been released.</span></span> <span data-ttu-id="c1538-107">Erişim ihlali belirleyici olmayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="c1538-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c1538-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="c1538-108">Cause</span></span>  
 <span data-ttu-id="c1538-109">Yönetilmeyen bir bileşen, yönetilen bir COM nesnesini doğru bir şekilde saymadığı takdirde, yönetilmeyen bileşen nesneye bir başvuru tuttuğunda, çalışma zamanı COM 'a sunulan bir yönetilen nesne toplayabilir.</span><span class="sxs-lookup"><span data-stu-id="c1538-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="c1538-110">Çalışma zamanı atık koleksiyonlar sırasında <xref:System.Runtime.InteropServices.Marshal.Release%2A> çağırır, bu nedenle Kullanıcı bileşeni atık toplama gerçekleşmeden önce nesneyi kullanıyorsa, henüz toplanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c1538-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="c1538-111">Bu, belirleyici olmayan bir ISM kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="c1538-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c1538-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c1538-112">Resolution</span></span>  
 <span data-ttu-id="c1538-113">Bu yardımcıyı etkinleştirmek, nesnenin koleksiyon için uygun olduğu zaman arasındaki süreyi azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> çağrılır, hangi yönetilmeyen bileşenin toplanan nesneye erişmeye çalıştığı aşağıda izlenmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c1538-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c1538-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c1538-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="c1538-115">Her iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c1538-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c1538-116">Çıktı</span><span class="sxs-lookup"><span data-stu-id="c1538-116">Output</span></span>  
 <span data-ttu-id="c1538-117">Bu MDA hiçbir çıkış üretmez.</span><span class="sxs-lookup"><span data-stu-id="c1538-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c1538-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1538-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1538-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1538-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c1538-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c1538-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c1538-121">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c1538-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="c1538-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="c1538-122">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
