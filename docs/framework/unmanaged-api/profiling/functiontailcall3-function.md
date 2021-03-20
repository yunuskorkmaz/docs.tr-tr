---
description: 'Daha fazla bilgi edinin: FunctionTailcall3 Işlevi'
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
ms.openlocfilehash: 4a67f218f0815ce6aff6ec4eda3d26ee2bf1fc3c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759462"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="728b1-103">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="728b1-103">FunctionTailcall3 Function</span></span>

<span data-ttu-id="728b1-104">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="728b1-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="728b1-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="728b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="728b1-106">Parameters</span></span>

<span data-ttu-id="728b1-107">`functionOrRemappedID` 'ndaki Bir tail çağrısı yapmak üzere olan şu anda yürütülmekte olan işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="728b1-107">`functionOrRemappedID` [in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="728b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="728b1-108">Remarks</span></span>  

 <span data-ttu-id="728b1-109">`FunctionTailcall3`Geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="728b1-109">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="728b1-110">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="728b1-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="728b1-111">`FunctionTailcall3`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="728b1-111">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="728b1-112">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="728b1-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="728b1-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="728b1-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="728b1-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="728b1-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="728b1-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="728b1-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="728b1-116">`FunctionTailcall3`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="728b1-116">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="728b1-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="728b1-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="728b1-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="728b1-118">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="728b1-119">`FunctionTailcall3`İşlev yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya hiçbir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="728b1-119">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="728b1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="728b1-120">Requirements</span></span>  

 <span data-ttu-id="728b1-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="728b1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="728b1-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="728b1-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="728b1-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="728b1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="728b1-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="728b1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728b1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="728b1-125">See also</span></span>

- [<span data-ttu-id="728b1-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="728b1-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="728b1-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="728b1-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="728b1-128">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="728b1-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="728b1-129">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="728b1-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="728b1-130">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="728b1-130">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="728b1-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="728b1-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="728b1-132">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="728b1-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="728b1-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="728b1-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="728b1-134">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="728b1-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="728b1-135">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="728b1-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
