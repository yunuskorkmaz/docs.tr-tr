---
title: "FunctionLeave3 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3
helpviewer_keywords: FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11aa67a03cfb88910704c0f1d2f586f8dbed7d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave3-function"></a><span data-ttu-id="07a16-102">FunctionLeave3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="07a16-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="07a16-103">Profil Oluşturucu denetim bir işlevinden döndürülen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="07a16-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07a16-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07a16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07a16-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="07a16-106">[in] Denetim döndürülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="07a16-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07a16-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07a16-107">Remarks</span></span>  
 <span data-ttu-id="07a16-108">`FunctionLeave3` Geri çağırma işlevi bildirir profil oluşturucu işlevleri adı verilir, ancak dönüş değeri denetleme desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="07a16-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="07a16-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlevin kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="07a16-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="07a16-110">`FunctionLeave3` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="07a16-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="07a16-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07a16-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="07a16-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="07a16-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="07a16-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07a16-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="07a16-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07a16-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="07a16-115">Uygulaması `FunctionLeave3` çöp toplama geciktirir çünkü bloğunu değil.</span><span class="sxs-lookup"><span data-stu-id="07a16-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="07a16-116">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulaması bir atık toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="07a16-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="07a16-117">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionLeave3` döndürür.</span><span class="sxs-lookup"><span data-stu-id="07a16-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="07a16-118">`FunctionLeave3` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde bir yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="07a16-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a16-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07a16-119">Requirements</span></span>  
 <span data-ttu-id="07a16-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07a16-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a16-121">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="07a16-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="07a16-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07a16-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07a16-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a16-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a16-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07a16-124">See Also</span></span>  
 [<span data-ttu-id="07a16-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="07a16-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="07a16-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="07a16-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="07a16-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="07a16-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="07a16-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="07a16-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="07a16-129">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="07a16-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="07a16-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="07a16-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="07a16-131">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="07a16-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="07a16-132">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="07a16-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="07a16-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="07a16-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="07a16-134">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="07a16-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
