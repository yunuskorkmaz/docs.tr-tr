---
title: Yönetilmeyen DLL İşlevlerini Kullanma
description: Yönetilmeyen DLL işlevlerini platform çağırma hizmetini kullanarak kullanın, bu, yönetilen kod çağrısı Yönetilmeyen işlevlerin DLL kitaplıklarında uygulanmasına olanak tanır.
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
ms.openlocfilehash: 880cbd4701ae4aee35038f6402b3beb70e60290c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622191"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="93cc9-103">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="93cc9-103">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="93cc9-104">Platform çağırma, yönetilen kodun, Windows API 'dakiler gibi dinamik bağlantı kitaplıkları (dll) içinde uygulanan yönetilmeyen işlevleri çağırmasına olanak sağlayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="93cc9-104">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="93cc9-105">İçe aktarılmış bir işlevi bulur ve çağırır ve bağımsız değişkenlerini (tamsayılar, dizeler, diziler, yapılar vb.) gerektiğinde birlikte çalışma sınırında sıralar.</span><span class="sxs-lookup"><span data-stu-id="93cc9-105">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="93cc9-106">Bu bölüm, yönetilmeyen DLL işlevleri tüketen ilişkili görevleri tanıtır ve platform çağırma hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="93cc9-106">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="93cc9-107">Aşağıdaki görevlere ek olarak, Genel hususlar ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.</span><span class="sxs-lookup"><span data-stu-id="93cc9-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="93cc9-108">İçe aktarılmış DLL işlevlerini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="93cc9-108">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="93cc9-109">[DLL 'lerdeki Işlevleri belirler](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="93cc9-109">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="93cc9-110">En düşük düzeyde, işlevin adını ve onu içeren DLL adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="93cc9-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="93cc9-111">[DLL işlevlerini barındıracak bir sınıf oluşturun](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="93cc9-111">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="93cc9-112">Mevcut bir sınıfı kullanabilir, her yönetilmeyen işlev için tek bir sınıf oluşturabilir veya ilgili yönetilmeyen işlevler kümesini içeren bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93cc9-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="93cc9-113">[Yönetilen kodda prototipler oluşturun](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="93cc9-113">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="93cc9-114">[Visual Basic] **Declare** ifadesini **Function** ve **lib** anahtar sözcükleriyle kullanın.</span><span class="sxs-lookup"><span data-stu-id="93cc9-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="93cc9-115">Nadir bazı durumlarda, **paylaşılan işlev** anahtar sözcükleriyle **DllImportAttribute** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93cc9-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="93cc9-116">Bu durumlar bu bölümde daha sonra açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93cc9-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="93cc9-117">Þ DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın.</span><span class="sxs-lookup"><span data-stu-id="93cc9-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="93cc9-118">Yöntemi **static** ve **extern** değiştiricilere göre işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="93cc9-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="93cc9-119">C++ DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın.</span><span class="sxs-lookup"><span data-stu-id="93cc9-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="93cc9-120">Sarmalayıcı metodunu veya işlevi **extern "C"** ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="93cc9-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="93cc9-121">[BIR DLL Işlevi çağırın](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="93cc9-121">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="93cc9-122">Yönetilen sınıfınıza, diğer yönetilen yöntemler gibi yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="93cc9-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="93cc9-123">[Yapıları geçirme](passing-structures.md) ve [geri çağırma işlevlerini uygulama](callback-functions.md) özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="93cc9-123">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="93cc9-124">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="93cc9-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="93cc9-125">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="93cc9-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="93cc9-126">Platform çağırma, içe aktarılmış işlevleri bulmak ve çalışma zamanında bağımsız değişkenlerini sıralamak için meta verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="93cc9-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="93cc9-127">Aşağıdaki çizim bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="93cc9-127">The following illustration shows this process.</span></span>  
  
 ![Platform çağırma çağrısını gösteren diyagram.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="93cc9-129">Platform Invoke yönetilmeyen bir işlevi çağırdığında, aşağıdaki eylem dizisini gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="93cc9-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="93cc9-130">İşlevi içeren DLL 'yi bulur.</span><span class="sxs-lookup"><span data-stu-id="93cc9-130">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="93cc9-131">DLL 'yi belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="93cc9-131">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="93cc9-132">Bellekteki işlevin adresini bulur ve bağımsız değişkenlerini yığına iter, verileri gereken şekilde sıralama.</span><span class="sxs-lookup"><span data-stu-id="93cc9-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93cc9-133">DLL 'yi bulma ve yükleme ve bellekteki işlevin adresini bulma işlemi yalnızca işlevin ilk çağrısında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="93cc9-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="93cc9-134">Denetimi yönetilmeyen işleve aktarır.</span><span class="sxs-lookup"><span data-stu-id="93cc9-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="93cc9-135">Platform çağırma, yönetilmeyen işlev tarafından yönetilen çağırana oluşturulan özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93cc9-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="93cc9-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93cc9-136">See also</span></span>

- [<span data-ttu-id="93cc9-137">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="93cc9-137">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="93cc9-138">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="93cc9-138">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="93cc9-139">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="93cc9-139">Interop Marshaling</span></span>](interop-marshaling.md)
