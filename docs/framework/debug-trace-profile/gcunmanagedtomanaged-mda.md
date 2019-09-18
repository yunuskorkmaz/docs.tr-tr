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
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052770"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="c2af9-102">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="c2af9-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="c2af9-103">Yönetilen `gcUnmanagedToManaged` hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c2af9-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c2af9-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c2af9-104">Symptoms</span></span>  
 <span data-ttu-id="c2af9-105">COM ve platform Invoke kullanılarak yönetilmeyen Kullanıcı bileşenlerini çalıştıran bir uygulama, CLR 'de belirleyici olmayan bir erişim ihlaline neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="c2af9-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c2af9-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="c2af9-106">Cause</span></span>  
 <span data-ttu-id="c2af9-107">Bir uygulama yönetilmeyen Kullanıcı bileşenleri çalıştırıyorsa, bu bileşenler atık toplanan yığını bozmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2af9-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="c2af9-108">Bu, çöp toplayıcı nesne grafiğine kılavuzluk etmeye çalıştığında CLR 'de erişim ihlaline neden olur.</span><span class="sxs-lookup"><span data-stu-id="c2af9-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c2af9-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c2af9-109">Resolution</span></span>  
 <span data-ttu-id="c2af9-110">Bu yardımcıyı etkinleştirmek, yönetilmeyen bileşenin atık toplanan yığını ihlal etmesiyle ilgili süreyi ve bir çöp toplamanın her yönetilen geçişten önce gerçekleşmesini zorlayarak meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="c2af9-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c2af9-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c2af9-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c2af9-112">Bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c2af9-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c2af9-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c2af9-113">Output</span></span>  
 <span data-ttu-id="c2af9-114">Bu MDA hiçbir çıkış üretmez.</span><span class="sxs-lookup"><span data-stu-id="c2af9-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c2af9-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c2af9-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2af9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2af9-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c2af9-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c2af9-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c2af9-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="c2af9-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="c2af9-119">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c2af9-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
