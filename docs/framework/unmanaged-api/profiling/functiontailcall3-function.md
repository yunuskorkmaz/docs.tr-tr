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
ms.openlocfilehash: 3bedb2c5f55f608b1153272437c0f55b730c2dfc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866862"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="9773b-102">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="9773b-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="9773b-103">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9773b-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9773b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9773b-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9773b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9773b-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="9773b-106">\[in] Şu anda yürütülmekte olan işlevin tanıtıcısı, kuyruk çağrısını yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9773b-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="9773b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9773b-107">Remarks</span></span>  
 <span data-ttu-id="9773b-108">`FunctionTailcall3` geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9773b-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="9773b-109">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9773b-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="9773b-110">`FunctionTailcall3` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9773b-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="9773b-111">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9773b-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="9773b-112">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="9773b-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="9773b-113">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9773b-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="9773b-114">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9773b-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9773b-115">Atık toplamayı ertelendirip `FunctionTailcall3` uygulanması engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="9773b-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="9773b-116">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="9773b-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9773b-117">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="9773b-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="9773b-118">`FunctionTailcall3` işlevi, yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9773b-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9773b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9773b-119">Requirements</span></span>  
 <span data-ttu-id="9773b-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9773b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9773b-121">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="9773b-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9773b-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9773b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9773b-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9773b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9773b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9773b-124">See also</span></span>

- [<span data-ttu-id="9773b-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="9773b-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="9773b-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="9773b-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="9773b-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="9773b-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="9773b-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="9773b-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="9773b-129">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="9773b-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9773b-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="9773b-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="9773b-131">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="9773b-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="9773b-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="9773b-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="9773b-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="9773b-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="9773b-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9773b-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
