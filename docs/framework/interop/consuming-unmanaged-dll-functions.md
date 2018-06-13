---
title: Yönetilmeyen DLL İşlevlerini Kullanma
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3166d6c95532706781188da0c56ebf9022038a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388384"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="ed933-102">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed933-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="ed933-103">Platform çağırma etkinleştirir Win32 API de gibi dinamik bağlantı kitaplıklarını (DLL'ler), uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ed933-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Win32 API.</span></span> <span data-ttu-id="ed933-104">Verilen işlevi çağırır bulur ve bağımsız değişkenleri (tamsayı, dize, diziler, yapıları ve benzeri) arasında birlikte çalışabilirlik sınır gerektiği şekilde sıralar.</span><span class="sxs-lookup"><span data-stu-id="ed933-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="ed933-105">Bu bölümde, yönetilmeyen DLL işlevlerini kullanma ile ilgili görevleri tanıtır ve çağırma platformu hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed933-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="ed933-106">Aşağıdaki görevlere ek olarak, genel konular ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.</span><span class="sxs-lookup"><span data-stu-id="ed933-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="ed933-107">Dışa aktarılan DLL işlevleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="ed933-107">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="ed933-108">[DLL'lerde işlevleri tanımlamak](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="ed933-109">En azından adını işlevi ve içerdiği DLL adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed933-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="ed933-110">[DLL işlevleri için bir sınıf oluşturun](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="ed933-111">Varolan bir sınıf kullanma, yönetilmeyen her işlev için tek bir sınıf oluşturun veya ilgili yönetilmeyen işlevler kümesi içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed933-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="ed933-112">[Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="ed933-113">[Visual Basic] Kullanım **Declare** deyimiyle **işlevi** ve **Lib** anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="ed933-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="ed933-114">Bazı nadir durumlarda, kullandığınız **DllImportAttribute** ile **paylaşılan işlevi** anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="ed933-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="ed933-115">Bu durumlarda, daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ed933-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="ed933-116">[C#] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="ed933-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="ed933-117">Yöntemiyle işaretlemek **statik** ve **extern** değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="ed933-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="ed933-118">[C++] Kullanım **DllImportAttribute** işlevini ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="ed933-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="ed933-119">Sarmalayıcı yöntemini işaretlemek veya ile işlev **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="ed933-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="ed933-120">[Bir DLL işlevi çağırma](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="ed933-121">Yönetilen herhangi bir yöntemini gibi yönetilen sınıfınız yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ed933-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="ed933-122">[Yapıları geçirme](../../../docs/framework/interop/passing-structures.md) ve [geri çağırma işlevlerini uygulama](../../../docs/framework/interop/callback-functions.md) özel durumları olan.</span><span class="sxs-lookup"><span data-stu-id="ed933-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="ed933-123">Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="ed933-124">Yakından platform çağırma</span><span class="sxs-lookup"><span data-stu-id="ed933-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="ed933-125">Platform çağırma dışarı aktarılan işlevleri bulun ve çalışma zamanında kendi bağımsız değişkenleri hazırlamak için meta verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed933-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="ed933-126">Aşağıdaki çizim bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ed933-126">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="ed933-127">![Platform Çağırma](../../../docs/framework/interop/media/pinvoke.gif "PInvoke")</span><span class="sxs-lookup"><span data-stu-id="ed933-127">![Platform invoke](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span></span>  
<span data-ttu-id="ed933-128">Yönetilmeyen DLL işlev çağrısı bir platform çağırma</span><span class="sxs-lookup"><span data-stu-id="ed933-128">A platform invoke call to an unmanaged DLL function</span></span>  
  
 <span data-ttu-id="ed933-129">Ne zaman platform çağırma yönetilmeyen bir işlevi çağırdığı sırasıyla aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ed933-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="ed933-130">İşlevi içeren DLL bulur.</span><span class="sxs-lookup"><span data-stu-id="ed933-130">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="ed933-131">DLL belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="ed933-131">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="ed933-132">İşlevin adresini bellekte bulur ve bağımsız değişkenlerini verileri gereken şekilde hazırlama yığına iter.</span><span class="sxs-lookup"><span data-stu-id="ed933-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed933-133">Bulma ve dll dosyasını yüklerken ve bellekte işlevin adresini bulmak işlevi yalnızca ilk çağrıda oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed933-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="ed933-134">Yönetilmeyen işlev aktarımları denetimi.</span><span class="sxs-lookup"><span data-stu-id="ed933-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="ed933-135">Platform çağırma yönetilen çağırana yönetilmeyen işlevi tarafından oluşturulan atar özel durumları.</span><span class="sxs-lookup"><span data-stu-id="ed933-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed933-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed933-136">See Also</span></span>  
 [<span data-ttu-id="ed933-137">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="ed933-137">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="ed933-138">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ed933-138">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="ed933-139">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ed933-139">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
