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
ms.openlocfilehash: 75a9a7174f105d99e9d1c9b220cfc5bf928d46ec
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866976"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="3f7ab-102">FunctionEnter3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f7ab-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="3f7ab-103">Denetim oluşturucuyu denetimin bir işleve geçtiğini bildirir ve yığın çerçevesini ve işlev bağımsız değişkenlerini almak için [ICorProfilerInfo3:: GetFunctionEnter3Info yöntemine](icorprofilerinfo3-getfunctionenter3info-method.md) geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f7ab-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f7ab-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="3f7ab-106">\[içinde] denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="3f7ab-107">\[, belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyicsahiptir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="3f7ab-108">Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f7ab-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f7ab-109">Remarks</span></span>  
 <span data-ttu-id="3f7ab-110">`FunctionEnter3WithInfo` geri çağırma yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun bağımsız değişken değerlerini incelemek için [ICorProfilerInfo3:: GetFunctionEnter3Info metodunu](icorprofilerinfo3-getfunctionenter3info-method.md) kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="3f7ab-111">Bağımsız değişken bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="3f7ab-112">Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="3f7ab-113">`FunctionEnter3WithInfo` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="3f7ab-114">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="3f7ab-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3f7ab-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3f7ab-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3f7ab-118">Atık toplamayı ertelendirip `FunctionEnter3WithInfo` uygulanması engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="3f7ab-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3f7ab-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter3WithInfo` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="3f7ab-121">`FunctionEnter3WithInfo` işlevi, yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7ab-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f7ab-122">Requirements</span></span>  
 <span data-ttu-id="3f7ab-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f7ab-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7ab-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="3f7ab-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3f7ab-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f7ab-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f7ab-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7ab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7ab-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f7ab-127">See also</span></span>

- [<span data-ttu-id="3f7ab-128">Getfunctionenter3ınfo</span><span class="sxs-lookup"><span data-stu-id="3f7ab-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="3f7ab-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="3f7ab-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="3f7ab-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="3f7ab-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="3f7ab-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3f7ab-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
