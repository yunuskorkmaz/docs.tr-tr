---
title: "FunctionLeave2 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave2
helpviewer_keywords: FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c2dd85e23a54a20920e30e22bc91f88a813be39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave2-function"></a><span data-ttu-id="4ec53-102">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ec53-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="4ec53-103">Profil oluşturucu işlevi çağırana hakkında bilgi döndürmek için ve yığın çerçevesi ve işlevi dönüş değeri hakkında bilgi sağlar bildirir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ec53-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ec53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ec53-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="4ec53-106">[in] Döndürüyor işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4ec53-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="4ec53-107">[in] Profil oluşturucu aracılığıyla daha önce belirtilen açmayla işlevi tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="4ec53-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="4ec53-108">[in] A `COR_PRF_FRAME_INFO` noktalarını yığın çerçevesi hakkında bilgi için değer.</span><span class="sxs-lookup"><span data-stu-id="4ec53-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="4ec53-109">Profil Oluşturucu uygulamasında bu yürütme altyapısında dön geçirilen bir donuk tanıtıcısı düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ec53-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="4ec53-110">[in] Bir işaretçi bir [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) yapısı işlevin dönüş değeri bellek konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="4ec53-111">Dönüş değeri bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağı ayarlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="4ec53-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi olay bayraklarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ec53-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ec53-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ec53-113">Remarks</span></span>  
 <span data-ttu-id="4ec53-114">Değerlerini `func` ve `retvalRange` parametreler sonra geçerli değildir `FunctionLeave2` değerleri değiştirebilir veya yok edilmesi için işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ec53-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="4ec53-115">`FunctionLeave2` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="4ec53-116">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4ec53-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="4ec53-117">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="4ec53-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="4ec53-118">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="4ec53-119">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec53-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4ec53-120">Uygulaması `FunctionLeave2` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="4ec53-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="4ec53-121">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ec53-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4ec53-122">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionLeave2` döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ec53-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="4ec53-123">Ayrıca, `FunctionLeave2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="4ec53-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec53-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ec53-124">Requirements</span></span>  
 <span data-ttu-id="4ec53-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ec53-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec53-126">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4ec53-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4ec53-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ec53-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ec53-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec53-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec53-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ec53-129">See Also</span></span>  
 [<span data-ttu-id="4ec53-130">FunctionEnter2 işlevi</span><span class="sxs-lookup"><span data-stu-id="4ec53-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="4ec53-131">FunctionTailcall2 işlevi</span><span class="sxs-lookup"><span data-stu-id="4ec53-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="4ec53-132">SetEnterLeaveFunctionHooks2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ec53-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="4ec53-133">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="4ec53-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
