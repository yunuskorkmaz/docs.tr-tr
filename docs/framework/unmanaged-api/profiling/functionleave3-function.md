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
ms.openlocfilehash: 32d86f19e9c50694c7d113195e6967645b710666
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866875"
---
# <a name="functionleave3-function"></a><span data-ttu-id="2dc3e-102">FunctionLeave3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="2dc3e-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="2dc3e-103">Denetim oluşturucuyu, denetimin bir işlevden döndürülmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dc3e-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dc3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2dc3e-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="2dc3e-106">\[in] denetimin döndürüldüğü işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2dc3e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dc3e-107">Remarks</span></span>  
 <span data-ttu-id="2dc3e-108">`FunctionLeave3` geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu ancak değer incelemesini desteklemiyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="2dc3e-109">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="2dc3e-110">`FunctionLeave3` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="2dc3e-111">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="2dc3e-112">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="2dc3e-113">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="2dc3e-114">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2dc3e-115">Atık toplamayı ertelendirip `FunctionLeave3` uygulanması engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="2dc3e-116">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2dc3e-117">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave3` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="2dc3e-118">`FunctionLeave3` işlevi, yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dc3e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dc3e-119">Requirements</span></span>  
 <span data-ttu-id="2dc3e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dc3e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dc3e-121">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="2dc3e-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2dc3e-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2dc3e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2dc3e-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dc3e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc3e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc3e-124">See also</span></span>

- [<span data-ttu-id="2dc3e-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="2dc3e-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="2dc3e-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="2dc3e-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="2dc3e-127">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="2dc3e-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="2dc3e-128">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="2dc3e-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="2dc3e-129">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="2dc3e-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="2dc3e-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="2dc3e-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="2dc3e-131">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="2dc3e-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="2dc3e-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="2dc3e-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="2dc3e-133">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="2dc3e-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="2dc3e-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2dc3e-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
