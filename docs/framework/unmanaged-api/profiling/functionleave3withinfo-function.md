---
title: FunctionLeave3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4304c933b9802ef565b8d18f1e04591e7fa83cb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189935"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="908ee-102">FunctionLeave3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="908ee-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="908ee-103">Profil Oluşturucu denetimi bir işlevden döndürülen uyarır ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctionleave3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) yığın çerçevesi ve dönüş değeri alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="908ee-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="908ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="908ee-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="908ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="908ee-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="908ee-106">[in] Denetim, döndürülen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="908ee-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="908ee-107">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="908ee-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="908ee-108">Bu işleyici, başarılı geri sırasında geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="908ee-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="908ee-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="908ee-109">Remarks</span></span>  
 <span data-ttu-id="908ee-110">`FunctionLeave3WithInfo` Geri çağırma yöntemi, profil oluşturucu işlevleri olarak adlandırılır ve kullanmak profil oluşturucu sağlar bildirir [Icorprofilerınfo3::getfunctionleave3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) denetlemeye dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="908ee-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="908ee-111">Dönüş değeri bilgilerini erişmeye `COR_PRF_ENABLE_FUNCTION_RETVAL` ayarlanacak bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="908ee-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="908ee-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve ardından [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.</span><span class="sxs-lookup"><span data-stu-id="908ee-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="908ee-113">`FunctionLeave3WithInfo` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="908ee-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="908ee-114">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="908ee-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="908ee-115">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="908ee-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="908ee-116">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="908ee-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="908ee-117">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="908ee-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="908ee-118">Uygulamasını `FunctionLeave3WithInfo` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="908ee-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="908ee-119">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="908ee-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="908ee-120">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionLeave3WithInfo` döndürür.</span><span class="sxs-lookup"><span data-stu-id="908ee-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="908ee-121">`FunctionLeave3WithInfo` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="908ee-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="908ee-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="908ee-122">Requirements</span></span>  
 <span data-ttu-id="908ee-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="908ee-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="908ee-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="908ee-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="908ee-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="908ee-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="908ee-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="908ee-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908ee-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="908ee-127">See also</span></span>

- [<span data-ttu-id="908ee-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="908ee-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="908ee-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="908ee-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="908ee-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="908ee-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="908ee-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="908ee-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="908ee-132">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="908ee-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="908ee-133">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="908ee-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="908ee-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="908ee-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="908ee-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="908ee-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="908ee-136">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="908ee-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="908ee-137">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="908ee-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="908ee-138">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="908ee-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
