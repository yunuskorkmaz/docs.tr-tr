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
ms.openlocfilehash: deae99f5bdc7c187997d4bad4957b2fcdccdc166
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051723"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="dd5e7-102">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="dd5e7-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="dd5e7-103">DLL işlevinin kimliği aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="dd5e7-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="dd5e7-104">İşlev adı veya sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="dd5e7-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="dd5e7-105">Uygulamanın bulunduğu DLL dosyasının adı</span><span class="sxs-lookup"><span data-stu-id="dd5e7-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="dd5e7-106">Örneğin, User32. dll ' de **MessageBox** işlevini belirtmek, Işlevi (**MessageBox**) ve konumunu (User32. dll, User32 veya User32) belirler.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="dd5e7-107">Microsoft Windows uygulama programlama arabirimi (Windows API), karakterleri ve dizeleri işleyen her bir işlevin iki sürümünü içerebilir: 1 baytlık karakter ANSI sürümü ve 2 baytlık karakter Unicode sürümü.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="dd5e7-108">Belirtilmediğinde, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alan tarafından temsil edilen karakter kümesi varsayılan olarak ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="dd5e7-109">Bazı işlevlerin ikiden fazla sürümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="dd5e7-110">**MessageBoxA** , **MESSAGEBOX** işlevi için ANSI giriş noktasıdır; **MessageBoxW** Unicode sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="dd5e7-111">Çeşitli komut satırı araçlarını çalıştırarak, User32. dll gibi belirli bir DLL için işlev adlarını listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="dd5e7-112">Örneğin, işlev adlarını almak için `dumpbin /exports user32.dll` veya `link /dump /exports user32.dll` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="dd5e7-113">Yeni adı DLL 'deki özgün giriş noktasına eşledikten sonra, yönetilmeyen bir işlevi kodunuzda dilediğiniz şekilde yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="dd5e7-114">Yönetilen kaynak kodunda yönetilmeyen DLL işlevini yeniden adlandırma yönergeleri için bkz. [giriş noktası belirtme](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="dd5e7-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="dd5e7-115">Platform çağırma, Windows API ve diğer dll 'Lerdeki işlevleri çağırarak işletim sisteminin önemli bir bölümünü denetlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="dd5e7-116">Windows API 'sine ek olarak, platform Invoke aracılığıyla kullanabileceğiniz çok sayıda başka API ve DLL vardır.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="dd5e7-117">Aşağıdaki tabloda, Windows API 'sinde yaygın olarak kullanılan birkaç dll açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="dd5e7-118">DLL</span><span class="sxs-lookup"><span data-stu-id="dd5e7-118">DLL</span></span>|<span data-ttu-id="dd5e7-119">Içeriklerin açıklaması</span><span class="sxs-lookup"><span data-stu-id="dd5e7-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="dd5e7-120">GDI32. dll</span><span class="sxs-lookup"><span data-stu-id="dd5e7-120">GDI32.dll</span></span>|<span data-ttu-id="dd5e7-121">Çizim ve yazı tipi yönetimi gibi cihaz çıktıları için Grafik Cihaz Arabirimi (GDI) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="dd5e7-122">Kernel32. dll</span><span class="sxs-lookup"><span data-stu-id="dd5e7-122">Kernel32.dll</span></span>|<span data-ttu-id="dd5e7-123">Bellek yönetimi ve kaynak işleme için alt düzey işletim sistemi işlevleri.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="dd5e7-124">User32. dll</span><span class="sxs-lookup"><span data-stu-id="dd5e7-124">User32.dll</span></span>|<span data-ttu-id="dd5e7-125">İleti işleme, zamanlayıcılar, menüler ve iletişimler için Windows yönetim işlevleri.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="dd5e7-126">Windows API 'SI ile ilgili tüm belgeler için bkz. Platform SDK 'Sı.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="dd5e7-127">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="dd5e7-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5e7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd5e7-128">See also</span></span>

- [<span data-ttu-id="dd5e7-129">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="dd5e7-129">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="dd5e7-130">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="dd5e7-130">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="dd5e7-131">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd5e7-131">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="dd5e7-132">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dd5e7-132">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="dd5e7-133">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="dd5e7-133">Calling a DLL Function</span></span>](calling-a-dll-function.md)
