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
ms.openlocfilehash: f2b2d5a935c2608b2315633538fc93dd62595558
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340041"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="67f02-102">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="67f02-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="67f02-103">Platform çağırma etkinleştirir olanlar Windows API gibi dinamik bağlantı kitaplıklarını (DLL'ler) uygulanan yönetilmeyen işlevleri çağırmak için kod yönetilen bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="67f02-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="67f02-104">Dışarı aktarılan bir işlevi çağırır bulur ve bağımsız değişkenlerinden (tamsayı, dizeler, diziler, yapılar ve benzeri) gerektiği gibi birlikte çalışabilirlik sınırında sürekliliğe devreder.</span><span class="sxs-lookup"><span data-stu-id="67f02-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="67f02-105">Bu bölümde, yönetilmeyen DLL işlevlerini kullanma ile ilgili görevleri tanıtır ve çağırma platformu hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67f02-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="67f02-106">Aşağıdaki görevlerin yanı sıra genel önemli noktalar ve ek bilgiler ve örnekler sağlayan bir bağlantı vardır.</span><span class="sxs-lookup"><span data-stu-id="67f02-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="67f02-107">Dışa aktarılan DLL işlevleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="67f02-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="67f02-108">[DLL'lerde işlevleri tanımlama](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="67f02-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="67f02-109">En düşük düzeyde, işlevin adını ve içerdiği DLL'in adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67f02-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="67f02-110">[DLL işlevleri için bir sınıf oluşturmanız](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="67f02-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="67f02-111">Varolan bir sınıfı kullanın, yönetilmeyen her işlev için bağımsız bir sınıf oluşturun veya ilgili yönetilmeyen işlevler bir dizi içeren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67f02-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="67f02-112">[Yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="67f02-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="67f02-113">[Visual Basic] Kullanım **Declare** deyimiyle **işlevi** ve **LIB** anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="67f02-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="67f02-114">Bazı nadir durumlarda, kullandığınız **DllImportAttribute** ile **paylaşılan işlevi** anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="67f02-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="67f02-115">Bu gibi durumlarda, daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="67f02-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="67f02-116">[C#] Kullanımı **DllImportAttribute** işlevi ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="67f02-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="67f02-117">Yöntemi işaretlemek **statik** ve **extern** değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="67f02-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="67f02-118">[C++] Kullanımı **DllImportAttribute** işlevi ve DLL tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="67f02-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="67f02-119">Sarmalayıcı yöntemini işaretlemek veya işlevini **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="67f02-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="67f02-120">[Bir DLL işlevini çağırmak](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="67f02-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="67f02-121">Yönetilen herhangi bir yöntemi gibi yönetilen sınıfınıza yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="67f02-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="67f02-122">[Yapıları geçirme](../../../docs/framework/interop/passing-structures.md) ve [geri çağırma işlevlerini uygulama](../../../docs/framework/interop/callback-functions.md) özel durumları olan.</span><span class="sxs-lookup"><span data-stu-id="67f02-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="67f02-123">Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="67f02-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="67f02-124">Yakından platform çağırma</span><span class="sxs-lookup"><span data-stu-id="67f02-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="67f02-125">Platform çağırma dışarı aktarılan işlevleri bulun ve bunların bağımsız değişkenleri, çalışma zamanında hazırlamak için meta verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="67f02-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="67f02-126">Aşağıdaki çizim bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="67f02-126">The following illustration shows this process.</span></span>  
  
 ![Çağırma çağrısı bir platform gösteren diyagram.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="67f02-128">Yönetilmeyen bir işlev çağırır olduğunda platform çağırma aşağıdaki eylemler dizisini gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="67f02-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="67f02-129">İşlevi içeren DLL bulur.</span><span class="sxs-lookup"><span data-stu-id="67f02-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="67f02-130">DLL belleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="67f02-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="67f02-131">Bellekte bir işlevin adresini bulur ve bağımsız olarak gerekli veri hazırlama yığına iter.</span><span class="sxs-lookup"><span data-stu-id="67f02-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67f02-132">İşlev yalnızca ilk çağrıda işlevin adresini bellekte bulma bulma ve DLL yüklenirken oluşur.</span><span class="sxs-lookup"><span data-stu-id="67f02-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="67f02-133">Yönetilmeyen işlev denetimine aktarımlarına.</span><span class="sxs-lookup"><span data-stu-id="67f02-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="67f02-134">Platform çağırma yönetilen çağırana yönetilmeyen işlevi tarafından oluşturulan oluşturur özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="67f02-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="67f02-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67f02-135">See also</span></span>

- [<span data-ttu-id="67f02-136">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="67f02-136">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="67f02-137">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="67f02-137">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="67f02-138">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="67f02-138">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
