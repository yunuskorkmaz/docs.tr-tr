---
description: 'Daha fazla bilgi edinin: FunctionLeave3 Işlevi'
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
ms.openlocfilehash: 9da68ffa2c54ada1437b3bef8bd6324c0791d610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687460"
---
# <a name="functionleave3-function"></a><span data-ttu-id="a47c6-103">FunctionLeave3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a47c6-103">FunctionLeave3 Function</span></span>

<span data-ttu-id="a47c6-104">Denetim oluşturucuyu, denetimin bir işlevden döndürülmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-104">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a47c6-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a47c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a47c6-106">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="a47c6-107">\[' de] denetimin döndürüldüğü işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a47c6-107">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a47c6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a47c6-108">Remarks</span></span>  

 <span data-ttu-id="a47c6-109">`FunctionLeave3`Geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu ancak değer incelemesini desteklemiyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-109">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="a47c6-110">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a47c6-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a47c6-111">`FunctionLeave3`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-111">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a47c6-112">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a47c6-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="a47c6-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a47c6-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a47c6-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a47c6-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a47c6-116">`FunctionLeave3`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-116">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a47c6-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="a47c6-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a47c6-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="a47c6-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="a47c6-119">`FunctionLeave3`İşlev yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya hiçbir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a47c6-119">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a47c6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a47c6-120">Requirements</span></span>  

 <span data-ttu-id="a47c6-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a47c6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a47c6-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a47c6-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a47c6-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a47c6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a47c6-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a47c6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a47c6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a47c6-125">See also</span></span>

- [<span data-ttu-id="a47c6-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a47c6-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="a47c6-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a47c6-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a47c6-128">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="a47c6-128">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a47c6-129">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="a47c6-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a47c6-130">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="a47c6-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a47c6-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a47c6-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a47c6-132">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="a47c6-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a47c6-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a47c6-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a47c6-134">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="a47c6-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a47c6-135">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a47c6-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
