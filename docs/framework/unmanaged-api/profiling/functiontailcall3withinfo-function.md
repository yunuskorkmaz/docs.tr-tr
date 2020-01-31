---
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
ms.openlocfilehash: 0aa43954c3e10d04524bf976d0dd3b29d2bc724c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866836"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="4c128-102">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="4c128-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="4c128-103">Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info yöntemine](icorprofilerinfo3-getfunctiontailcall3info-method.md) geçirilebilecek bir tanıtıcı sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="4c128-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c128-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c128-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c128-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c128-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="4c128-106">\[in] Şu anda yürütülmekte olan işlevin tanıtıcısı, kuyruk çağrısını yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c128-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="4c128-107">\[, belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyicsahiptir.</span><span class="sxs-lookup"><span data-stu-id="4c128-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="4c128-108">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4c128-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c128-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c128-109">Remarks</span></span>  
 <span data-ttu-id="4c128-110">`FunctionTailcall3WithInfo` geri çağırma yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun yığın çerçevesini incelemek için [ICorProfilerInfo3:: GetFunctionTailcall3Info metodunu](icorprofilerinfo3-getfunctiontailcall3info-method.md) kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4c128-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="4c128-111">Yığın çerçevesi bilgilerine erişmek için `COR_PRF_ENABLE_FRAME_INFO` bayrağının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c128-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="4c128-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4c128-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4c128-113">`FunctionTailcall3WithInfo` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c128-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="4c128-114">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c128-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="4c128-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="4c128-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="4c128-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4c128-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="4c128-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c128-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4c128-118">Atık toplamayı ertelendirip `FunctionTailcall3WithInfo` uygulanması engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="4c128-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="4c128-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="4c128-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4c128-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="4c128-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="4c128-121">Ayrıca, Functiontailcall3withınfo işlevi yönetilen koda çağrı veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c128-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c128-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c128-122">Requirements</span></span>  
 <span data-ttu-id="4c128-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c128-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c128-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="4c128-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4c128-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c128-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c128-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c128-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c128-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c128-127">See also</span></span>

- [<span data-ttu-id="4c128-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4c128-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="4c128-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="4c128-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="4c128-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="4c128-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4c128-131">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="4c128-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4c128-132">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="4c128-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="4c128-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="4c128-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="4c128-134">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="4c128-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="4c128-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="4c128-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4c128-136">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="4c128-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="4c128-137">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4c128-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
