---
title: "FunctionEnter İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="3dace-102">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="3dace-102">FunctionEnter Function</span></span>
<span data-ttu-id="3dace-103">Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3dace-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dace-104">`FunctionEnter` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır ve kullanımını performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dace-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="3dace-105">Kullanım [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="3dace-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dace-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dace-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dace-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dace-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3dace-108">[in] Denetim geçirilen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3dace-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dace-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dace-109">Remarks</span></span>  
 <span data-ttu-id="3dace-110">`FunctionEnter` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3dace-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="3dace-111">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3dace-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3dace-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="3dace-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="3dace-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3dace-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="3dace-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3dace-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3dace-115">Uygulaması `FunctionEnter` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="3dace-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3dace-116">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dace-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3dace-117">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionEnter` döndürür.</span><span class="sxs-lookup"><span data-stu-id="3dace-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="3dace-118">Ayrıca, `FunctionEnter` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="3dace-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dace-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dace-119">Requirements</span></span>  
 <span data-ttu-id="3dace-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dace-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dace-121">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3dace-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3dace-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dace-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dace-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3dace-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dace-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dace-124">See Also</span></span>  
 [<span data-ttu-id="3dace-125">FunctionEnter2 işlevi</span><span class="sxs-lookup"><span data-stu-id="3dace-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="3dace-126">FunctionLeave2 işlevi</span><span class="sxs-lookup"><span data-stu-id="3dace-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="3dace-127">FunctionTailcall2 işlevi</span><span class="sxs-lookup"><span data-stu-id="3dace-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="3dace-128">SetEnterLeaveFunctionHooks2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dace-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="3dace-129">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="3dace-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
