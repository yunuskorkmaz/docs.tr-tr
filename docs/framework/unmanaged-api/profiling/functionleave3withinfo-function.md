---
title: FunctionLeave3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: 235bae64fe5e6a534f2a650050c6c9ad4aa8fe84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500630"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="139e3-102">FunctionLeave3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="139e3-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="139e3-103">Denetim oluşturucuyu bir işlevden döndürülmekte olduğunu bildirir ve yığın çerçevesini ve dönüş değerini almak için [ICorProfilerInfo3:: GetFunctionLeave3Info yöntemine](icorprofilerinfo3-getfunctionleave3info-method.md) geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="139e3-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="139e3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="139e3-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="139e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="139e3-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="139e3-106">\[' de] denetimin döndürüldüğü işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="139e3-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="139e3-107">\[' de] belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyici.</span><span class="sxs-lookup"><span data-stu-id="139e3-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="139e3-108">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="139e3-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="139e3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="139e3-109">Remarks</span></span>  
 <span data-ttu-id="139e3-110">`FunctionLeave3WithInfo`Geri arama yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun döndürülen değeri incelemek Için [ICorProfilerInfo3:: GetFunctionLeave3Info metodunu](icorprofilerinfo3-getfunctionleave3info-method.md) kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="139e3-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="139e3-111">Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="139e3-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="139e3-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="139e3-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="139e3-113">`FunctionLeave3WithInfo`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="139e3-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="139e3-114">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="139e3-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="139e3-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="139e3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="139e3-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="139e3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="139e3-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="139e3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="139e3-118">`FunctionLeave3WithInfo`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="139e3-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="139e3-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="139e3-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="139e3-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="139e3-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="139e3-121">`FunctionLeave3WithInfo`İşlev yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya hiçbir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="139e3-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="139e3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="139e3-122">Requirements</span></span>  
 <span data-ttu-id="139e3-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="139e3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="139e3-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="139e3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="139e3-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="139e3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="139e3-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="139e3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139e3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="139e3-127">See also</span></span>

- [<span data-ttu-id="139e3-128">Getfunctionleave3ınfo</span><span class="sxs-lookup"><span data-stu-id="139e3-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="139e3-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="139e3-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="139e3-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="139e3-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="139e3-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="139e3-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="139e3-132">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="139e3-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="139e3-133">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="139e3-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="139e3-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="139e3-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="139e3-135">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="139e3-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="139e3-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="139e3-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="139e3-137">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="139e3-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="139e3-138">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="139e3-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
