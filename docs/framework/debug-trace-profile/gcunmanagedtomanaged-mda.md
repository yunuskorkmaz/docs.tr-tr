---
title: gcUnmanagedToManaged MDA
description: .NET 'teki gcManagedToUnmanaged Managed hata ayıklama Yardımcısı ' nı gözden geçirin. Bu MDA, yönetilen koda geçiş sırasında atık yığın bozulması nedeniyle etkinleştirilebilir.
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
ms.openlocfilehash: 61fbdbf0d3941aa3e876748ae4d76cd7ad0c0977
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244229"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="b3270-104">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="b3270-104">gcUnmanagedToManaged MDA</span></span>

<span data-ttu-id="b3270-105">`gcUnmanagedToManaged`Yönetilen hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b3270-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b3270-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b3270-106">Symptoms</span></span>  

 <span data-ttu-id="b3270-107">COM ve platform Invoke kullanılarak yönetilmeyen Kullanıcı bileşenlerini çalıştıran bir uygulama, CLR 'de belirleyici olmayan bir erişim ihlaline neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="b3270-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b3270-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b3270-108">Cause</span></span>  

 <span data-ttu-id="b3270-109">Bir uygulama yönetilmeyen Kullanıcı bileşenleri çalıştırıyorsa, bu bileşenler atık toplanan yığını bozmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3270-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="b3270-110">Bu, çöp toplayıcı nesne grafiğine kılavuzluk etmeye çalıştığında CLR 'de erişim ihlaline neden olur.</span><span class="sxs-lookup"><span data-stu-id="b3270-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b3270-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b3270-111">Resolution</span></span>  

 <span data-ttu-id="b3270-112">Bu yardımcıyı etkinleştirmek, yönetilmeyen bileşenin atık toplanan yığını ihlal etmesiyle ilgili süreyi ve bir çöp toplamanın her yönetilen geçişten önce gerçekleşmesini zorlayarak meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="b3270-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b3270-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b3270-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="b3270-114">Bir iş parçacığı yönetilmeyenden yönetilen koddan her geçiş yaptığında çöp toplamaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b3270-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b3270-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="b3270-115">Output</span></span>  

 <span data-ttu-id="b3270-116">Bu MDA hiçbir çıkış üretmez.</span><span class="sxs-lookup"><span data-stu-id="b3270-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b3270-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b3270-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3270-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3270-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b3270-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b3270-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b3270-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="b3270-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="b3270-121">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="b3270-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
