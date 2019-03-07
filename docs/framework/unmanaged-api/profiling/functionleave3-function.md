---
title: FunctionLeave3 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56d9f449c11989091def5e6d34670f5b00f5c0bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484387"
---
# <a name="functionleave3-function"></a><span data-ttu-id="06f2b-102">FunctionLeave3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="06f2b-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="06f2b-103">Profil Oluşturucu denetimi bir işlevden döndürülen uyarır.</span><span class="sxs-lookup"><span data-stu-id="06f2b-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06f2b-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06f2b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06f2b-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="06f2b-106">[in] Denetim, döndürülen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="06f2b-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f2b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06f2b-107">Remarks</span></span>  
 <span data-ttu-id="06f2b-108">`FunctionLeave3` Geri çağırma işlevini bildirir profil oluşturucu işlevleri adı verilir, ancak dönüş değeri incelemesi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="06f2b-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="06f2b-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlev, kaydedilecek.</span><span class="sxs-lookup"><span data-stu-id="06f2b-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="06f2b-110">`FunctionLeave3` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06f2b-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="06f2b-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="06f2b-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="06f2b-112">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="06f2b-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="06f2b-113">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="06f2b-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="06f2b-114">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="06f2b-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="06f2b-115">Uygulamasını `FunctionLeave3` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="06f2b-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="06f2b-116">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="06f2b-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="06f2b-117">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionLeave3` döndürür.</span><span class="sxs-lookup"><span data-stu-id="06f2b-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="06f2b-118">`FunctionLeave3` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="06f2b-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f2b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06f2b-119">Requirements</span></span>  
 <span data-ttu-id="06f2b-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f2b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f2b-121">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="06f2b-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="06f2b-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06f2b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06f2b-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f2b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f2b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06f2b-124">See also</span></span>
- [<span data-ttu-id="06f2b-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="06f2b-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="06f2b-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="06f2b-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="06f2b-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="06f2b-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="06f2b-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="06f2b-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="06f2b-129">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="06f2b-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="06f2b-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="06f2b-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="06f2b-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="06f2b-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="06f2b-132">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="06f2b-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="06f2b-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="06f2b-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="06f2b-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="06f2b-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
