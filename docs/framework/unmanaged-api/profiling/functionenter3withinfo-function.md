---
title: FunctionEnter3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: ff4b32185e604611eaaead2847c11bc139d405a6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500695"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="f9423-102">FunctionEnter3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f9423-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="f9423-103">Denetim oluşturucuyu denetimin bir işleve geçtiğini bildirir ve yığın çerçevesini ve işlev bağımsız değişkenlerini almak için [ICorProfilerInfo3:: GetFunctionEnter3Info yöntemine](icorprofilerinfo3-getfunctionenter3info-method.md) geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9423-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9423-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9423-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9423-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9423-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="f9423-106">\[' de] denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f9423-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="f9423-107">\[' de] belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyici.</span><span class="sxs-lookup"><span data-stu-id="f9423-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f9423-108">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f9423-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9423-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9423-109">Remarks</span></span>  
 <span data-ttu-id="f9423-110">`FunctionEnter3WithInfo`Geri arama yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun bağımsız değişken değerlerini incelemek Için [ICorProfilerInfo3:: GetFunctionEnter3Info metodunu](icorprofilerinfo3-getfunctionenter3info-method.md) kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9423-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="f9423-111">Bağımsız değişken bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9423-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="f9423-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f9423-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f9423-113">`FunctionEnter3WithInfo`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9423-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="f9423-114">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9423-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f9423-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="f9423-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f9423-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f9423-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f9423-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9423-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f9423-118">`FunctionEnter3WithInfo`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f9423-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f9423-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="f9423-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f9423-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="f9423-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="f9423-121">`FunctionEnter3WithInfo`İşlev yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya hiçbir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9423-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9423-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9423-122">Requirements</span></span>  
 <span data-ttu-id="f9423-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9423-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9423-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="f9423-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f9423-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9423-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9423-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9423-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9423-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9423-127">See also</span></span>

- [<span data-ttu-id="f9423-128">Getfunctionenter3ınfo</span><span class="sxs-lookup"><span data-stu-id="f9423-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="f9423-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f9423-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="f9423-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f9423-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="f9423-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f9423-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
