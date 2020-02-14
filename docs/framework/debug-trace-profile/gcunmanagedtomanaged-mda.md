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
ms.openlocfilehash: dd4080870ae88da8d4e2055369cd36f3981f2eac
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216449"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="3af6f-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="3af6f-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="3af6f-103">`gcUnmanagedToManaged` yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3af6f-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3af6f-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="3af6f-104">Symptoms</span></span>  
 <span data-ttu-id="3af6f-105">COM ve platform Invoke kullanılarak yönetilmeyen Kullanıcı bileşenlerini çalıştıran bir uygulama, CLR 'de belirleyici olmayan bir erişim ihlaline neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="3af6f-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3af6f-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="3af6f-106">Cause</span></span>  
 <span data-ttu-id="3af6f-107">Bir uygulama yönetilmeyen Kullanıcı bileşenleri çalıştırıyorsa, bu bileşenler atık toplanan yığını bozmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3af6f-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="3af6f-108">Bu, çöp toplayıcı nesne grafiğine kılavuzluk etmeye çalıştığında CLR 'de erişim ihlaline neden olur.</span><span class="sxs-lookup"><span data-stu-id="3af6f-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3af6f-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="3af6f-109">Resolution</span></span>  
 <span data-ttu-id="3af6f-110">Bu yardımcıyı etkinleştirmek, yönetilmeyen bileşenin atık toplanan yığını ihlal etmesiyle ilgili süreyi ve bir çöp toplamanın her yönetilen geçişten önce gerçekleşmesini zorlayarak meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="3af6f-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3af6f-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="3af6f-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="3af6f-112">Bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3af6f-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3af6f-113">Çıktı</span><span class="sxs-lookup"><span data-stu-id="3af6f-113">Output</span></span>  
 <span data-ttu-id="3af6f-114">Bu MDA hiçbir çıkış üretmez.</span><span class="sxs-lookup"><span data-stu-id="3af6f-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3af6f-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3af6f-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3af6f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3af6f-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3af6f-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="3af6f-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3af6f-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="3af6f-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="3af6f-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="3af6f-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
