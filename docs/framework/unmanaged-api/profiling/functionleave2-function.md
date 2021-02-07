---
description: 'Daha fazla bilgi edinin: FunctionLeave2 Işlevi'
title: FunctionLeave2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: 475def9af448182003ef36782a84d501a9f2661d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687577"
---
# <a name="functionleave2-function"></a><span data-ttu-id="d8e7a-103">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d8e7a-103">FunctionLeave2 Function</span></span>

<span data-ttu-id="d8e7a-104">Profil oluşturucuya bir işlevin çağırana dönmek üzere olduğunu bildirir ve yığın çerçevesi ve işlev dönüş değeri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-104">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e7a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8e7a-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8e7a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8e7a-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="d8e7a-107">\[içinde] döndüren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-107">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="d8e7a-108">\[' de] profil oluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevi aracılığıyla belirttiği yeniden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-108">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="d8e7a-109">\[' de] `COR_PRF_FRAME_INFO` yığın çerçevesi hakkındaki bilgileri gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="d8e7a-110">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="d8e7a-111">\[' de] işlevin dönüş değerinin bellek konumunu belirten [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="d8e7a-112">Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-112">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="d8e7a-113">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8e7a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8e7a-114">Remarks</span></span>  

 <span data-ttu-id="d8e7a-115">Ve parametrelerinin değerleri, `func` `retvalRange` `FunctionLeave2` değerler değişeceğinden veya yok edileceği için döndüğünde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-115">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="d8e7a-116">`FunctionLeave2`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-116">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="d8e7a-117">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d8e7a-118">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d8e7a-119">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d8e7a-120">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d8e7a-121">, `FunctionLeave2` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-121">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d8e7a-122">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d8e7a-123">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-123">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="d8e7a-124">Ayrıca, `FunctionLeave2` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-124">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8e7a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8e7a-125">Requirements</span></span>  

 <span data-ttu-id="d8e7a-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8e7a-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8e7a-127">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="d8e7a-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d8e7a-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8e7a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8e7a-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8e7a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e7a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e7a-130">See also</span></span>

- [<span data-ttu-id="d8e7a-131">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d8e7a-131">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d8e7a-132">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d8e7a-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="d8e7a-133">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8e7a-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="d8e7a-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d8e7a-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
