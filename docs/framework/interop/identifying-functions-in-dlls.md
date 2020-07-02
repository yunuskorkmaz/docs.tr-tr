---
title: DLL'lerde İşlevleri Tanımlama
description: Dll 'Lerdeki işlevleri belirler. Bir DLL işlevinin kimliği, bir işlev adından veya sıra değerinden ve uygulamanın bulunduğu DLL dosyası adından oluşur.
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
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622737"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="f925c-104">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f925c-104">Identifying Functions in DLLs</span></span>
<span data-ttu-id="f925c-105">DLL işlevinin kimliği aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="f925c-105">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="f925c-106">İşlev adı veya sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="f925c-106">Function name or ordinal</span></span>  
  
- <span data-ttu-id="f925c-107">Uygulamanın bulunduğu DLL dosyasının adı</span><span class="sxs-lookup"><span data-stu-id="f925c-107">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="f925c-108">Örneğin, User32.dll **MessageBox** işlevini belirtmek, Işlevi (**MessageBox**) ve konumunu (User32.dll, User32 veya User32) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f925c-108">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="f925c-109">Microsoft Windows uygulama programlama arabirimi (Windows API), karakterleri ve dizeleri işleyen her bir işlevin iki sürümünü içerebilir: 1 baytlık karakter ANSI sürümü ve 2 baytlık karakter Unicode sürümü.</span><span class="sxs-lookup"><span data-stu-id="f925c-109">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="f925c-110">Belirtilmediğinde, alan tarafından temsil edilen karakter kümesi varsayılan olarak <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="f925c-110">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="f925c-111">Bazı işlevlerin ikiden fazla sürümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f925c-111">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="f925c-112">**MessageBoxA** , **MESSAGEBOX** işlevi için ANSI giriş noktasıdır; **MessageBoxW** Unicode sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f925c-112">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="f925c-113">Çeşitli komut satırı araçlarını çalıştırarak, user32.dll gibi belirli bir DLL için işlev adlarını listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f925c-113">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="f925c-114">Örneğin, `dumpbin /exports user32.dll` `link /dump /exports user32.dll` işlev adlarını almak için veya kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f925c-114">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="f925c-115">Yeni adı DLL 'deki özgün giriş noktasına eşledikten sonra, yönetilmeyen bir işlevi kodunuzda dilediğiniz şekilde yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f925c-115">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="f925c-116">Yönetilen kaynak kodunda yönetilmeyen DLL işlevini yeniden adlandırma yönergeleri için bkz. [giriş noktası belirtme](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="f925c-116">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="f925c-117">Platform çağırma, Windows API ve diğer dll 'Lerdeki işlevleri çağırarak işletim sisteminin önemli bir bölümünü denetlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f925c-117">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="f925c-118">Windows API 'sine ek olarak, platform Invoke aracılığıyla kullanabileceğiniz çok sayıda başka API ve DLL vardır.</span><span class="sxs-lookup"><span data-stu-id="f925c-118">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="f925c-119">Aşağıdaki tabloda, Windows API 'sinde yaygın olarak kullanılan birkaç dll açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f925c-119">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="f925c-120">DLL</span><span class="sxs-lookup"><span data-stu-id="f925c-120">DLL</span></span>|<span data-ttu-id="f925c-121">Içeriklerin açıklaması</span><span class="sxs-lookup"><span data-stu-id="f925c-121">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="f925c-122">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="f925c-122">GDI32.dll</span></span>|<span data-ttu-id="f925c-123">Çizim ve yazı tipi yönetimi gibi cihaz çıktıları için Grafik Cihaz Arabirimi (GDI) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f925c-123">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="f925c-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f925c-124">Kernel32.dll</span></span>|<span data-ttu-id="f925c-125">Bellek yönetimi ve kaynak işleme için alt düzey işletim sistemi işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f925c-125">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="f925c-126">User32.dll</span><span class="sxs-lookup"><span data-stu-id="f925c-126">User32.dll</span></span>|<span data-ttu-id="f925c-127">İleti işleme, zamanlayıcılar, menüler ve iletişimler için Windows yönetim işlevleri.</span><span class="sxs-lookup"><span data-stu-id="f925c-127">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="f925c-128">Windows API 'SI ile ilgili tüm belgeler için bkz. Platform SDK 'Sı.</span><span class="sxs-lookup"><span data-stu-id="f925c-128">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="f925c-129">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f925c-129">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f925c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f925c-130">See also</span></span>

- [<span data-ttu-id="f925c-131">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f925c-131">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="f925c-132">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="f925c-132">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="f925c-133">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f925c-133">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="f925c-134">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f925c-134">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f925c-135">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="f925c-135">Calling a DLL Function</span></span>](calling-a-dll-function.md)
