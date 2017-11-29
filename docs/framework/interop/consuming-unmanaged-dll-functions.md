---
title: "Yönetilmeyen DLL İşlevlerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec93728566d6aa16d4b9b15b171d79831cc0dbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="92bb9-102">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="92bb9-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="92bb9-103">Platform çağırma etkinleştirir Win32 API de gibi dinamik bağlantı kitaplıklarını (DLL'ler), uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="92bb9-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Win32 API.</span></span> <span data-ttu-id="92bb9-104">Verilen işlevi çağırır bulur ve bağımsız değişkenleri (tamsayı, dize, diziler, yapıları ve benzeri) arasında birlikte çalışabilirlik sınır gerektiği şekilde sıralar.</span><span class="sxs-lookup"><span data-stu-id="92bb9-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span> <span data-ttu-id="92bb9-105">Bu hizmet hakkında daha fazla bilgi için bkz: [A daha yakın bakabilir Platform Çağırma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span><span class="sxs-lookup"><span data-stu-id="92bb9-105">For more information about this service, see [A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span></span>  
  
 <span data-ttu-id="92bb9-106">Bu bölüm, yönetilmeyen DLL işlevlerini kullanma ile ilgili çeşitli görevleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="92bb9-106">This section introduces several tasks associated with consuming unmanaged DLL functions.</span></span> <span data-ttu-id="92bb9-107">Aşağıdaki görevlere ek olarak, genel konular ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.</span><span class="sxs-lookup"><span data-stu-id="92bb9-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="92bb9-108">Dışa aktarılan DLL işlevleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="92bb9-108">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="92bb9-109">[DLL'lerde işlevleri tanımlamak](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="92bb9-109">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="92bb9-110">En azından adını işlevi ve içerdiği DLL adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="92bb9-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="92bb9-111">[DLL işlevleri için bir sınıf oluşturun](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="92bb9-111">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="92bb9-112">Varolan bir sınıf kullanma, yönetilmeyen her işlev için tek bir sınıf oluşturun veya ilgili yönetilmeyen işlevler kümesi içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92bb9-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="92bb9-113">[Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="92bb9-113">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="92bb9-114">[Visual Basic] Kullanım **Declare** deyimiyle **işlevi** ve **Lib** anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="92bb9-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="92bb9-115">Bazı nadir durumlarda, kullandığınız **DllImportAttribute** ile **paylaşılan işlevi** anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="92bb9-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="92bb9-116">Bu durumlarda, daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="92bb9-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="92bb9-117">[C#] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="92bb9-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="92bb9-118">Yöntemiyle işaretlemek **statik** ve **extern** değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="92bb9-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="92bb9-119">[C++] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="92bb9-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="92bb9-120">Sarmalayıcı yöntemini işaretlemek veya ile işlev **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="92bb9-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="92bb9-121">[Bir DLL işlevi çağırma](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="92bb9-121">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="92bb9-122">Yönetilen herhangi bir yöntemini gibi yönetilen sınıfınız yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="92bb9-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="92bb9-123">[Yapıları geçirme](../../../docs/framework/interop/passing-structures.md) ve [geri çağırma işlevlerini uygulama](../../../docs/framework/interop/callback-functions.md) özel durumları olan.</span><span class="sxs-lookup"><span data-stu-id="92bb9-123">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="92bb9-124">Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="92bb9-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="92bb9-125">Yakından platform çağırma</span><span class="sxs-lookup"><span data-stu-id="92bb9-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="92bb9-126">Platform çağırma dışarı aktarılan işlevleri bulun ve çalışma zamanında kendi bağımsız değişkenleri hazırlamak için meta verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="92bb9-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="92bb9-127">Aşağıdaki çizim bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="92bb9-127">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="92bb9-128">![Platform Çağırma](../../../docs/framework/interop/media/pinvoke.gif "PInvoke")</span><span class="sxs-lookup"><span data-stu-id="92bb9-128">![Platform invoke](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span></span>  
<span data-ttu-id="92bb9-129">Yönetilmeyen DLL işlev çağrısı bir platform çağırma</span><span class="sxs-lookup"><span data-stu-id="92bb9-129">A platform invoke call to an unmanaged DLL function</span></span>  
  
 <span data-ttu-id="92bb9-130">Ne zaman platform çağırma yönetilmeyen bir işlevi çağırdığı sırasıyla aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="92bb9-130">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="92bb9-131">İşlevi içeren DLL bulur.</span><span class="sxs-lookup"><span data-stu-id="92bb9-131">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="92bb9-132">DLL belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="92bb9-132">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="92bb9-133">İşlevin adresini bellekte bulur ve bağımsız değişkenlerini verileri gereken şekilde hazırlama yığına iter.</span><span class="sxs-lookup"><span data-stu-id="92bb9-133">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92bb9-134">Bulma ve dll dosyasını yüklerken ve bellekte işlevin adresini bulmak işlevi yalnızca ilk çağrıda oluşur.</span><span class="sxs-lookup"><span data-stu-id="92bb9-134">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="92bb9-135">Yönetilmeyen işlev aktarımları denetimi.</span><span class="sxs-lookup"><span data-stu-id="92bb9-135">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="92bb9-136">Platform çağırma yönetilen çağırana yönetilmeyen işlevi tarafından oluşturulan atar özel durumları.</span><span class="sxs-lookup"><span data-stu-id="92bb9-136">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92bb9-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92bb9-137">See Also</span></span>  
 [<span data-ttu-id="92bb9-138">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="92bb9-138">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="92bb9-139">Platform çağırma örnekleri</span><span class="sxs-lookup"><span data-stu-id="92bb9-139">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="92bb9-140">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="92bb9-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="92bb9-141">Yönetilmeyen DLL işlevlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="92bb9-141">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
