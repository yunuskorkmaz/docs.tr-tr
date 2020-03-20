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
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399975"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="bb7f8-102">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bb7f8-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="bb7f8-103">Platform çağırma, yönetilen kodun Windows API'dakiler gibi dinamik bağlantı kitaplıklarında (DL'lerde) uygulanan yönetilmeyen işlevleri çağırmasını sağlayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="bb7f8-104">Dışa aktarılan bir işlevi bulur ve çağırır ve gerektiğinde interişlem sınırı boyunca bağımsız değişkenlerini (karşıtlar, dizeleri, diziler, yapılar vb.) sıralar.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="bb7f8-105">Bu bölümde, yönetilmeyen DLL işlevlerinin tüketilmesiyle ilişkili görevler tanıtılmış ve platform çağırma hakkında daha fazla bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="bb7f8-106">Aşağıdaki görevlere ek olarak, genel hususlar ve ek bilgi ve örnekler sağlayan bir bağlantı vardır.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="bb7f8-107">Dışa aktarılan DLL işlevlerini tüketmek için</span><span class="sxs-lookup"><span data-stu-id="bb7f8-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="bb7f8-108">[DLs işlevlerini tanımlayın.](identifying-functions-in-dlls.md)</span><span class="sxs-lookup"><span data-stu-id="bb7f8-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="bb7f8-109">En az düzeyde, işlevin adını ve onu içeren DLL'nin adını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="bb7f8-110">[DLL işlevlerini tutmak için bir sınıf oluşturun.](creating-a-class-to-hold-dll-functions.md)</span><span class="sxs-lookup"><span data-stu-id="bb7f8-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="bb7f8-111">Varolan bir sınıfı kullanabilir, her yönetilmeyen işlev için ayrı bir sınıf oluşturabilir veya ilgili yönetilmeyen işlevler kümesi içeren bir sınıf oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="bb7f8-112">[Yönetilen kodda prototipler oluşturun.](creating-prototypes-in-managed-code.md)</span><span class="sxs-lookup"><span data-stu-id="bb7f8-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="bb7f8-113">[Visual Basic] **İşlev** ve **Lib** anahtar kelimeleriyle **Bildir ifadesini** kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="bb7f8-114">Bazı nadir durumlarda, **Paylaşılan İşlev** anahtar kelimeleri ile **DllImportAttribute** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="bb7f8-115">Bu olgular daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="bb7f8-116">[C#] DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="bb7f8-117">Yöntemi **statik** ve **extern** değiştiriciler ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="bb7f8-118">[C++] DLL ve işlevi tanımlamak için **DllImportAttribute** kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="bb7f8-119">Sarma makinesi yöntemini veya işlevini **extern "C"** ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="bb7f8-120">[Bir DLL işlevini arayın.](calling-a-dll-function.md)</span><span class="sxs-lookup"><span data-stu-id="bb7f8-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="bb7f8-121">Yönetilen sınıfınızdaki yöntemi, diğer yönetilen yöntemlerde olduğu gibi arayın.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="bb7f8-122">[Yapıları n geçirilmesi](passing-structures.md) ve [geri arama işlevlerinin uygulanması](callback-functions.md) özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="bb7f8-123">Nasıl inşa edilebildiğini gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, [Bkz. Platform Invoke ile Verileri Mareşalleme.](marshaling-data-with-platform-invoke.md)</span><span class="sxs-lookup"><span data-stu-id="bb7f8-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="bb7f8-124">Platform çağırmaya daha yakından bakmak</span><span class="sxs-lookup"><span data-stu-id="bb7f8-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="bb7f8-125">Platform, dışa aktarılan işlevleri bulmak ve bağımsız değişkenlerini çalışma zamanında mareşallemek için meta verilere dayanır.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="bb7f8-126">Aşağıdaki çizim bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-126">The following illustration shows this process.</span></span>  
  
 ![Platform çağrısı çağrısını gösteren diyagram.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="bb7f8-128">Platform yönetilmeyen bir işlev çağırdığında, aşağıdaki eylem sırasını gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="bb7f8-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="bb7f8-129">İşleviçeren DLL'yi bulur.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="bb7f8-130">DLL'yi belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="bb7f8-131">Bellekteki işlevin adresini bulur ve gerektiğinde verileri sıralayarak bağımsız değişkenlerini yığına iter.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bb7f8-132">DLL'nin bulunması ve yüklenmesi ve bellekteki işlevin adresinin bulunması yalnızca işlevin ilk çağrısında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="bb7f8-133">Denetimi yönetilmeyen işleve aktarın.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="bb7f8-134">Platform çağırma, yönetilen arayaniçin yönetilmeyen işlev tarafından oluşturulan özel durumlar atar.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb7f8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb7f8-135">See also</span></span>

- [<span data-ttu-id="bb7f8-136">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="bb7f8-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="bb7f8-137">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="bb7f8-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="bb7f8-138">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="bb7f8-138">Interop Marshaling</span></span>](interop-marshaling.md)
