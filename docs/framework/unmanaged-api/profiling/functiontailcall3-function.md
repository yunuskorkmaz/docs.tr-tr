---
title: FunctionTailcall3 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 636ff5613b2681a73986cc5bfe9a28954f014588
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155486"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="c3511-102">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3511-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="c3511-103">Profil Oluşturucu, yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c3511-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3511-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3511-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3511-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3511-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="c3511-106">[in] Bir kuyruk çağrısı yapmak üzere olan yürütülmekte olan işlevin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="c3511-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3511-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3511-107">Remarks</span></span>  
 <span data-ttu-id="c3511-108">`FunctionTailcall3` İşlevleri adlandırıldığı gibi profil oluşturucu geri çağırma işlevini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c3511-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="c3511-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlev, kaydedilecek.</span><span class="sxs-lookup"><span data-stu-id="c3511-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c3511-110">`FunctionTailcall3` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3511-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="c3511-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3511-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="c3511-112">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="c3511-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="c3511-113">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3511-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="c3511-114">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c3511-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c3511-115">Uygulamasını `FunctionTailcall3` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="c3511-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="c3511-116">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3511-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c3511-117">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionTailcall3` döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3511-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="c3511-118">`FunctionTailcall3` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="c3511-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3511-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3511-119">Requirements</span></span>  
 <span data-ttu-id="c3511-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3511-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3511-121">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c3511-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c3511-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3511-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c3511-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c3511-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3511-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3511-124">See also</span></span>

- [<span data-ttu-id="c3511-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c3511-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="c3511-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c3511-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="c3511-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="c3511-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="c3511-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c3511-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="c3511-129">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3511-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c3511-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="c3511-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="c3511-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c3511-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="c3511-132">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="c3511-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c3511-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="c3511-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="c3511-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c3511-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
