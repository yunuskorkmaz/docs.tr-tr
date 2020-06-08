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
ms.openlocfilehash: f076044b44859cc39d90be528ee6648f5eaa626c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500591"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="435ca-102">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="435ca-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="435ca-103">Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info yöntemine](icorprofilerinfo3-getfunctiontailcall3info-method.md) geçirilebilecek bir tanıtıcı sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="435ca-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="435ca-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="435ca-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="435ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="435ca-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="435ca-106">\[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="435ca-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="435ca-107">\[' de] belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyici.</span><span class="sxs-lookup"><span data-stu-id="435ca-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="435ca-108">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="435ca-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="435ca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="435ca-109">Remarks</span></span>  
 <span data-ttu-id="435ca-110">`FunctionTailcall3WithInfo`Geri arama yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun yığın çerçevesini incelemek Için [ICorProfilerInfo3:: GetFunctionTailcall3Info metodunu](icorprofilerinfo3-getfunctiontailcall3info-method.md) kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="435ca-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="435ca-111">Yığın çerçevesi bilgilerine erişmek için `COR_PRF_ENABLE_FRAME_INFO` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="435ca-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="435ca-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="435ca-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="435ca-113">`FunctionTailcall3WithInfo`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="435ca-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="435ca-114">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="435ca-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="435ca-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="435ca-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="435ca-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="435ca-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="435ca-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="435ca-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="435ca-118">`FunctionTailcall3WithInfo`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="435ca-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="435ca-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="435ca-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="435ca-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="435ca-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="435ca-121">Ayrıca, Functiontailcall3withınfo işlevi yönetilen koda çağrı veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="435ca-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="435ca-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="435ca-122">Requirements</span></span>  
 <span data-ttu-id="435ca-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="435ca-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="435ca-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="435ca-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="435ca-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="435ca-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="435ca-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="435ca-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435ca-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="435ca-127">See also</span></span>

- [<span data-ttu-id="435ca-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="435ca-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="435ca-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="435ca-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="435ca-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="435ca-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="435ca-131">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="435ca-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="435ca-132">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="435ca-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="435ca-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="435ca-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="435ca-134">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="435ca-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="435ca-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="435ca-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="435ca-136">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="435ca-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="435ca-137">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="435ca-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
