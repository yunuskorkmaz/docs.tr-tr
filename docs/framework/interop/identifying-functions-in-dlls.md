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
ms.openlocfilehash: c4c56712460d772426a2d8d6d328cba9bb03373d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648671"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="0998c-102">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0998c-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="0998c-103">Bir DLL işlevini kimliğini aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="0998c-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="0998c-104">İşlev adı veya sıra</span><span class="sxs-lookup"><span data-stu-id="0998c-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="0998c-105">Uygulama bulunabilir DLL dosyasının adı</span><span class="sxs-lookup"><span data-stu-id="0998c-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="0998c-106">Örneğin, belirten **MessageBox** User32.dll işlevinde işlevi tanımlar (**MessageBox**) ve konumu (User32.dll, User32 veya user32).</span><span class="sxs-lookup"><span data-stu-id="0998c-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="0998c-107">Microsoft Windows uygulama programlama arabirimi (Windows API) karakterleri ve dizeleri işleyen her işlevin iki sürümü içermelidir: 1-bayt karakter ANSI sürümü ve 2-bayt karakter Unicode sürümü.</span><span class="sxs-lookup"><span data-stu-id="0998c-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="0998c-108">Belirtilmediğinde, karakter kümesini temsil ettiği <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> ANSI varsayılan alan.</span><span class="sxs-lookup"><span data-stu-id="0998c-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="0998c-109">Bazı işlevler, ikiden fazla sürümleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0998c-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="0998c-110">**MessageBoxA** ANSI giriş noktası için **MessageBox** işlev; **MessageBoxW** Unicode sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0998c-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="0998c-111">İşlev adları, user32.dll gibi belirli bir DLL için çeşitli komut satırı araçları'nı çalıştırarak listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0998c-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="0998c-112">Örneğin, kullanabileceğiniz `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` işlev adlarını elde edilir.</span><span class="sxs-lookup"><span data-stu-id="0998c-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="0998c-113">Yönetilmeyen bir işlev özgün DLL giriş noktası için yeni adı eşleme sürece kodunuzun içinde dilediğiniz şekilde yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0998c-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="0998c-114">Yönetilen kaynak kodunda bir yönetilmeyen DLL işlevi yeniden adlandırma ile ilgili yönergeler için bkz: [giriş noktası belirtme](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="0998c-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="0998c-115">Platform çağırma etkinleştirir Windows API ve diğer DLL'leri çağırarak işletim sisteminin önemli bir bölümünü denetlemenizi işlevleri.</span><span class="sxs-lookup"><span data-stu-id="0998c-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="0998c-116">Windows API yanı sıra diğer birçok API vardır ve platformu kullanılabilir DLL'ler çağırma.</span><span class="sxs-lookup"><span data-stu-id="0998c-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="0998c-117">Aşağıdaki tablo bazı yaygın olarak kullanılan dll dosyaları Windows API açıklar.</span><span class="sxs-lookup"><span data-stu-id="0998c-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="0998c-118">DLL</span><span class="sxs-lookup"><span data-stu-id="0998c-118">DLL</span></span>|<span data-ttu-id="0998c-119">İçeriği açıklaması</span><span class="sxs-lookup"><span data-stu-id="0998c-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="0998c-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="0998c-120">GDI32.dll</span></span>|<span data-ttu-id="0998c-121">Grafik cihaz arabirimi (GDI) işlevleri için çıktı çizme ve yazı tipi Yönetim için olanlar gibi cihaz.</span><span class="sxs-lookup"><span data-stu-id="0998c-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="0998c-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0998c-122">Kernel32.dll</span></span>|<span data-ttu-id="0998c-123">Bellek yönetimi ve kaynak işleme işlevleri alt düzey işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="0998c-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="0998c-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="0998c-124">User32.dll</span></span>|<span data-ttu-id="0998c-125">İleti işleme, zamanlayıcıları, menüler ve iletişim için Windows Yönetim işlevleri.</span><span class="sxs-lookup"><span data-stu-id="0998c-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="0998c-126">Windows API ile ilgili kapsamlı belgeler için bkz.</span><span class="sxs-lookup"><span data-stu-id="0998c-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="0998c-127">Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="0998c-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0998c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0998c-128">See also</span></span>

- [<span data-ttu-id="0998c-129">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="0998c-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="0998c-130">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="0998c-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)
- [<span data-ttu-id="0998c-131">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0998c-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="0998c-132">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0998c-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="0998c-133">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="0998c-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
