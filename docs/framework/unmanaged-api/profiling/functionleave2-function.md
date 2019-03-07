---
title: FunctionLeave2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9985b5a5547097c0474eb3a5797388d1444083e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471595"
---
# <a name="functionleave2-function"></a><span data-ttu-id="500a9-102">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="500a9-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="500a9-103">Profil Oluşturucu bildirir: bir işlev hakkında çağırana döndürmesi için ve yığın çerçeve ve işlev dönüş değeri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="500a9-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="500a9-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="500a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="500a9-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="500a9-106">[in] Döndüren işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="500a9-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="500a9-107">[in] Profil Oluşturucu ile daha önce belirtilen işlevi yeniden eşlenen tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="500a9-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="500a9-108">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="500a9-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="500a9-109">Profil Oluşturucu bu geri yürütme altyapısı geçirilebilir donuk bir işleyici olarak düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="500a9-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="500a9-110">[in] Bir işaretçi bir [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) işlevin dönüş değerini bellek konumunu belirten yapısı.</span><span class="sxs-lookup"><span data-stu-id="500a9-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="500a9-111">Dönüş değeri bilgilerini erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağı ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="500a9-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="500a9-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayrakları ayarlamanızı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="500a9-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="500a9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="500a9-113">Remarks</span></span>  
 <span data-ttu-id="500a9-114">Değerlerini `func` ve `retvalRange` parametreler sonra geçerli değildir `FunctionLeave2` işlevi, değerleri değiştirebilir veya yok nedeniyle döndürür.</span><span class="sxs-lookup"><span data-stu-id="500a9-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="500a9-115">`FunctionLeave2` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="500a9-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="500a9-116">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="500a9-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="500a9-117">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="500a9-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="500a9-118">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="500a9-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="500a9-119">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="500a9-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="500a9-120">Uygulamasını `FunctionLeave2` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="500a9-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="500a9-121">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="500a9-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="500a9-122">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionLeave2` döndürür.</span><span class="sxs-lookup"><span data-stu-id="500a9-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="500a9-123">Ayrıca, `FunctionLeave2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="500a9-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="500a9-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="500a9-124">Requirements</span></span>  
 <span data-ttu-id="500a9-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="500a9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500a9-126">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="500a9-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="500a9-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="500a9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="500a9-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="500a9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500a9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="500a9-129">See also</span></span>
- [<span data-ttu-id="500a9-130">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="500a9-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="500a9-131">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="500a9-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="500a9-132">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="500a9-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="500a9-133">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="500a9-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
