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
ms.openlocfilehash: 8d7c226d26d677a8b10df29e0343b71682c46699
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427363"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="1ead3-102">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="1ead3-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="1ead3-103">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ead3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ead3-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ead3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ead3-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="1ead3-106">'ndaki Bir tail çağrısı yapmak üzere olan şu anda yürütülmekte olan işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1ead3-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ead3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ead3-107">Remarks</span></span>  
 <span data-ttu-id="1ead3-108">`FunctionTailcall3` geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="1ead3-109">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ead3-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="1ead3-110">`FunctionTailcall3` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="1ead3-111">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="1ead3-112">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="1ead3-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="1ead3-113">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1ead3-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="1ead3-114">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="1ead3-115">Atık toplamayı ertelendirip `FunctionTailcall3` uygulanması engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="1ead3-116">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="1ead3-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="1ead3-117">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="1ead3-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="1ead3-118">`FunctionTailcall3` işlevi, yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ead3-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ead3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ead3-119">Requirements</span></span>  
 <span data-ttu-id="1ead3-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ead3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ead3-121">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="1ead3-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1ead3-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ead3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ead3-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ead3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ead3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ead3-124">See also</span></span>

- [<span data-ttu-id="1ead3-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="1ead3-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="1ead3-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="1ead3-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="1ead3-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="1ead3-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="1ead3-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="1ead3-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="1ead3-129">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="1ead3-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="1ead3-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="1ead3-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="1ead3-131">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="1ead3-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="1ead3-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="1ead3-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="1ead3-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="1ead3-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="1ead3-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1ead3-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
