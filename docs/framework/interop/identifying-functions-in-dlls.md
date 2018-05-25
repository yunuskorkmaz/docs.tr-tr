---
title: DLL'lerde İşlevleri Tanımlama
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc160678817266dc649f60dc3f2cc77044c05691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="07e57-102">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="07e57-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="07e57-103">DLL işlevini kimliğini aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="07e57-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="07e57-104">İşlev adı veya sıra</span><span class="sxs-lookup"><span data-stu-id="07e57-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="07e57-105">Uygulama bulunabilir DLL dosyasının adı</span><span class="sxs-lookup"><span data-stu-id="07e57-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="07e57-106">Örneğin, belirten **MessageBox** User32.dll işlevinde işlevi tanımlar (**MessageBox**) ve konumunu (User32.dll, User32 veya user32).</span><span class="sxs-lookup"><span data-stu-id="07e57-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="07e57-107">Microsoft Windows uygulama programlama arabirimi (Win32 API) karakterleri ve dizeleri işleme her işlev iki sürümü içerebilir: 1-bayt karakter ANSI sürümü ve 2-bayt karakter Unicode sürümü.</span><span class="sxs-lookup"><span data-stu-id="07e57-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="07e57-108">Karakter kümesi belirtilmemiş olduğunda temsil ettiği <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alan, ANSI varsayılanlara.</span><span class="sxs-lookup"><span data-stu-id="07e57-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="07e57-109">Bazı işlevler ikiden fazla sürümleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="07e57-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="07e57-110">**MessageBoxA** ANSI giriş noktası için **MessageBox** işlev; **MessageBoxW** Unicode sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="07e57-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="07e57-111">Çeşitli komut satırı araçları çalıştırarak user32.dll gibi belirli bir DLL için işlev adlarını listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07e57-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="07e57-112">Örneğin, kullanabileceğiniz `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` işlev adları elde edilir.</span><span class="sxs-lookup"><span data-stu-id="07e57-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="07e57-113">DLL özgün giriş noktası için yeni bir ad eşleme sürece ne olursa olsun, kodunuzun içinde ister yönetilmeyen işlev yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07e57-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="07e57-114">Yönetilen kaynak kodunda yönetilmeyen DLL işlev yeniden adlandırma ile ilgili yönergeler için bkz: [giriş noktası belirtme](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="07e57-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="07e57-115">Platform çağırma etkinleştirir çağırarak işletim sisteminin önemli bir kısmını denetlemek için işlevleri Win32 API ve diğer DLL'ler.</span><span class="sxs-lookup"><span data-stu-id="07e57-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="07e57-116">Win32 API yanı sıra platformu aracılığıyla kullanılabilir DLL'ler çağırma ve diğer pek çok API'leri vardır.</span><span class="sxs-lookup"><span data-stu-id="07e57-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="07e57-117">Aşağıdaki tabloda bazı yaygın olarak kullanılan dll dosyaları Win32 API içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07e57-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="07e57-118">DLL</span><span class="sxs-lookup"><span data-stu-id="07e57-118">DLL</span></span>|<span data-ttu-id="07e57-119">İçeriği açıklaması</span><span class="sxs-lookup"><span data-stu-id="07e57-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="07e57-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="07e57-120">GDI32.dll</span></span>|<span data-ttu-id="07e57-121">Grafik cihaz arabirimi (GDI) işlevleri çıktı çizim ve yazı tipi yönetimi için olanlar gibi cihaz için.</span><span class="sxs-lookup"><span data-stu-id="07e57-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="07e57-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="07e57-122">Kernel32.dll</span></span>|<span data-ttu-id="07e57-123">Bellek yönetimi ve kaynak işleme için alt düzey işletim sistemi işlevleri.</span><span class="sxs-lookup"><span data-stu-id="07e57-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="07e57-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="07e57-124">User32.dll</span></span>|<span data-ttu-id="07e57-125">İleti işleme, zamanlayıcılar, menüleri ve iletişim için Windows Yönetim işlevleri.</span><span class="sxs-lookup"><span data-stu-id="07e57-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="07e57-126">Win32 API üzerindeki tüm belgeler için bkz.</span><span class="sxs-lookup"><span data-stu-id="07e57-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="07e57-127">Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="07e57-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e57-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07e57-128">See Also</span></span>  
 [<span data-ttu-id="07e57-129">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="07e57-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="07e57-130">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="07e57-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="07e57-131">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07e57-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="07e57-132">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07e57-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="07e57-133">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="07e57-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
