---
description: 'Daha fazla bilgi edinin: Functiontailcall3withınfo Işlevi'
title: FunctionTailcall3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: efa8b2e965ba4a365bbd72db4c5af69db006f6d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648512"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="6af56-103">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="6af56-103">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="6af56-104">Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info yöntemine](icorprofilerinfo3-getfunctiontailcall3info-method.md) geçirilebilecek bir tanıtıcı sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6af56-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af56-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6af56-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af56-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6af56-106">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="6af56-107">\[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6af56-107">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="6af56-108">\[' de] belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyici.</span><span class="sxs-lookup"><span data-stu-id="6af56-108">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6af56-109">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6af56-109">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6af56-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6af56-110">Remarks</span></span>  

 <span data-ttu-id="6af56-111">`FunctionTailcall3WithInfo`Geri arama yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun yığın çerçevesini incelemek Için [ICorProfilerInfo3:: GetFunctionTailcall3Info metodunu](icorprofilerinfo3-getfunctiontailcall3info-method.md) kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6af56-111">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="6af56-112">Yığın çerçevesi bilgilerine erişmek için `COR_PRF_ENABLE_FRAME_INFO` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af56-112">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="6af56-113">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6af56-113">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6af56-114">`FunctionTailcall3WithInfo`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af56-114">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="6af56-115">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af56-115">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6af56-116">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="6af56-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6af56-117">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6af56-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6af56-118">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af56-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6af56-119">`FunctionTailcall3WithInfo`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6af56-119">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="6af56-120">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="6af56-120">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6af56-121">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="6af56-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="6af56-122">Ayrıca, Functiontailcall3withınfo işlevi yönetilen koda çağrı veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6af56-122">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af56-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6af56-123">Requirements</span></span>  

 <span data-ttu-id="6af56-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af56-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af56-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="6af56-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6af56-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6af56-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6af56-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af56-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af56-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6af56-128">See also</span></span>

- [<span data-ttu-id="6af56-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6af56-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="6af56-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6af56-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="6af56-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6af56-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="6af56-132">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="6af56-132">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="6af56-133">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="6af56-133">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="6af56-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6af56-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="6af56-135">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="6af56-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="6af56-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="6af56-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="6af56-137">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="6af56-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="6af56-138">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6af56-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
