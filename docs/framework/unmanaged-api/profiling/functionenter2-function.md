---
title: FunctionEnter2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825da3a09f8b8013ffecaedfee0dce2362c8a7b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227814"
---
# <a name="functionenter2-function"></a><span data-ttu-id="28cd9-102">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28cd9-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="28cd9-103">Profil Oluşturucu bildirir: denetim bir işleve geçirilir ve çerçeve ve işlev bağımsız değişkenleri yığın hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="28cd9-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="28cd9-104">Bu işlevin yerini [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="28cd9-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cd9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28cd9-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28cd9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28cd9-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="28cd9-107">[in] Denetimin geçtiğini işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="28cd9-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="28cd9-108">[in] Profil oluşturucu kullanılarak daha önce belirtilen işlevi yeniden eşlenen tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="28cd9-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="28cd9-109">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="28cd9-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="28cd9-110">Profil Oluşturucu bu geri yürütme altyapısı geçirilebilir donuk bir işleyici olarak düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28cd9-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="28cd9-111">[in] Bir işaretçi bir [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısı, işlev bağımsız bellekte konumları belirtir.</span><span class="sxs-lookup"><span data-stu-id="28cd9-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="28cd9-112">Bağımsız değişken bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağı ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28cd9-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="28cd9-113">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayrakları ayarlamanızı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28cd9-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28cd9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28cd9-114">Remarks</span></span>  
 <span data-ttu-id="28cd9-115">Değerlerini `func` ve `argumentInfo` parametreler sonra geçerli değildir `FunctionEnter2` işlevi, değerleri değiştirebilir veya yok nedeniyle döndürür.</span><span class="sxs-lookup"><span data-stu-id="28cd9-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="28cd9-116">`FunctionEnter2` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28cd9-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="28cd9-117">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="28cd9-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="28cd9-118">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="28cd9-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="28cd9-119">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28cd9-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="28cd9-120">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="28cd9-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="28cd9-121">Uygulamasını `FunctionEnter2` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="28cd9-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="28cd9-122">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="28cd9-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="28cd9-123">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionEnter2` döndürür.</span><span class="sxs-lookup"><span data-stu-id="28cd9-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="28cd9-124">Ayrıca, `FunctionEnter2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="28cd9-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cd9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28cd9-125">Requirements</span></span>  
 <span data-ttu-id="28cd9-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28cd9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28cd9-127">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="28cd9-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="28cd9-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28cd9-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="28cd9-129">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="28cd9-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28cd9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28cd9-130">See also</span></span>

- [<span data-ttu-id="28cd9-131">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28cd9-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="28cd9-132">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28cd9-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="28cd9-133">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28cd9-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="28cd9-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="28cd9-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
