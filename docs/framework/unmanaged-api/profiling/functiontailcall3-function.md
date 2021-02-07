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
ms.openlocfilehash: 07ab49e8aeccdd82680a677c8b94e8a0c075d242
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687304"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="5abea-103">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="5abea-103">FunctionTailcall3 Function</span></span>

<span data-ttu-id="5abea-104">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5abea-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5abea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5abea-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5abea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5abea-106">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="5abea-107">\[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5abea-107">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="5abea-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5abea-108">Remarks</span></span>  

 <span data-ttu-id="5abea-109">`FunctionTailcall3`Geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5abea-109">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="5abea-110">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5abea-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="5abea-111">`FunctionTailcall3`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5abea-111">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="5abea-112">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5abea-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="5abea-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="5abea-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="5abea-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5abea-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="5abea-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5abea-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5abea-116">`FunctionTailcall3`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="5abea-116">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="5abea-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="5abea-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5abea-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="5abea-118">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="5abea-119">`FunctionTailcall3`İşlev yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya hiçbir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5abea-119">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5abea-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5abea-120">Requirements</span></span>  

 <span data-ttu-id="5abea-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5abea-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5abea-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="5abea-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5abea-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5abea-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5abea-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5abea-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abea-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5abea-125">See also</span></span>

- [<span data-ttu-id="5abea-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="5abea-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="5abea-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="5abea-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="5abea-128">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="5abea-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="5abea-129">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="5abea-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="5abea-130">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="5abea-130">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="5abea-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="5abea-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="5abea-132">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="5abea-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="5abea-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="5abea-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="5abea-134">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="5abea-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="5abea-135">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5abea-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
