---
title: "FunctionTailcall3WithInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3WithInfo
helpviewer_keywords: FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c22f00678f707df04a69104fedef87aa6d5e3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="6df4e-102">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="6df4e-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="6df4e-103">Başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere şu anda yürütülen işlevidir profil oluşturucu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctiontailcall3ınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) almak için yığın çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="6df4e-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df4e-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6df4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6df4e-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="6df4e-106">[in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6df4e-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6df4e-107">[in] Verilen yığın çerçevesi ilgili bilgileri temsil eder donuk işleci.</span><span class="sxs-lookup"><span data-stu-id="6df4e-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6df4e-108">Bu tanıtıcı geçirilen yalnızca geri çağırma sırasında geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6df4e-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df4e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df4e-109">Remarks</span></span>  
 <span data-ttu-id="6df4e-110">`FunctionTailcall3WithInfo` Geri çağırma yöntemi olarak işlevler olarak adlandırılır ve kullanmak profil oluşturucu sağlar profil oluşturucu bildirir [Icorprofilerınfo3::getfunctiontailcall3ınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) yığın çerçevesi incelemek için.</span><span class="sxs-lookup"><span data-stu-id="6df4e-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="6df4e-111">Yığın çerçevesi bilgilere erişmek için `COR_PRF_ENABLE_FRAME_INFO` bayrağı ayarlanmış olması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="6df4e-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="6df4e-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve sonra kullanmak için [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.</span><span class="sxs-lookup"><span data-stu-id="6df4e-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6df4e-113">`FunctionTailcall3WithInfo` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6df4e-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="6df4e-114">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6df4e-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6df4e-115">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="6df4e-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="6df4e-116">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6df4e-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="6df4e-117">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6df4e-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6df4e-118">Uygulaması `FunctionTailcall3WithInfo` çöp toplama geciktirir çünkü bloğunu değil.</span><span class="sxs-lookup"><span data-stu-id="6df4e-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="6df4e-119">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulaması bir atık toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6df4e-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6df4e-120">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall3WithInfo` döndürür.</span><span class="sxs-lookup"><span data-stu-id="6df4e-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="6df4e-121">Ayrıca, Functiontailcall3withınfo işlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde bir yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="6df4e-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df4e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df4e-122">Requirements</span></span>  
 <span data-ttu-id="6df4e-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df4e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df4e-124">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6df4e-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6df4e-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6df4e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6df4e-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df4e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df4e-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6df4e-127">See Also</span></span>  
 [<span data-ttu-id="6df4e-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6df4e-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="6df4e-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6df4e-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="6df4e-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6df4e-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="6df4e-131">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="6df4e-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="6df4e-132">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="6df4e-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="6df4e-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6df4e-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="6df4e-134">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="6df4e-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="6df4e-135">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="6df4e-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="6df4e-136">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="6df4e-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="6df4e-137">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="6df4e-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
