---
title: "FunctionTailcall3 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3
helpviewer_keywords: FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5d274c966a345e0e2984018bcd8aa1e2dade03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="fd0b3-102">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="fd0b3-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="fd0b3-103">Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd0b3-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd0b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd0b3-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="fd0b3-106">[in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd0b3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd0b3-107">Remarks</span></span>  
 <span data-ttu-id="fd0b3-108">`FunctionTailcall3` Geri çağırma işlevi işlevleri adlı gibi profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="fd0b3-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlevin kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fd0b3-110">`FunctionTailcall3` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="fd0b3-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="fd0b3-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="fd0b3-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="fd0b3-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fd0b3-115">Uygulaması `FunctionTailcall3` çöp toplama geciktirir çünkü bloğunu değil.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="fd0b3-116">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulaması bir atık toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fd0b3-117">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall3` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="fd0b3-118">`FunctionTailcall3` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde bir yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0b3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd0b3-119">Requirements</span></span>  
 <span data-ttu-id="fd0b3-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd0b3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0b3-121">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fd0b3-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fd0b3-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd0b3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd0b3-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0b3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0b3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd0b3-124">See Also</span></span>  
 [<span data-ttu-id="fd0b3-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="fd0b3-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="fd0b3-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fd0b3-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="fd0b3-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="fd0b3-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="fd0b3-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="fd0b3-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="fd0b3-129">Functiontailcall3withınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="fd0b3-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="fd0b3-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="fd0b3-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="fd0b3-131">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="fd0b3-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="fd0b3-132">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="fd0b3-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="fd0b3-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="fd0b3-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="fd0b3-134">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="fd0b3-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
