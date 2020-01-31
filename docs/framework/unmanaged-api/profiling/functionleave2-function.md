---
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
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866937"
---
# <a name="functionleave2-function"></a><span data-ttu-id="a4d29-102">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4d29-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="a4d29-103">Profil oluşturucuya bir işlevin çağırana dönmek üzere olduğunu bildirir ve yığın çerçevesi ve işlev dönüş değeri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4d29-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d29-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4d29-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="a4d29-106">\[içinde] döndüren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a4d29-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="a4d29-107">içinde \[], profil oluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevi ile belirttiği yeniden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a4d29-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="a4d29-108">\[içinde, yığın çerçevesi hakkındaki bilgileri gösteren bir `COR_PRF_FRAME_INFO` değeri.</span><span class="sxs-lookup"><span data-stu-id="a4d29-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="a4d29-109">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="a4d29-110">\[, işlevin dönüş değerinin bellek konumunu belirten [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="a4d29-111">Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="a4d29-112">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4d29-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4d29-113">Remarks</span></span>  
 <span data-ttu-id="a4d29-114">Değerler değişeceğinden veya yok edileceği için, `FunctionLeave2` işlevi döndüğünde `func` ve `retvalRange` parametrelerinin değerleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="a4d29-115">`FunctionLeave2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="a4d29-116">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="a4d29-117">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="a4d29-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a4d29-118">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a4d29-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a4d29-119">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a4d29-120">`FunctionLeave2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="a4d29-121">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="a4d29-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a4d29-122">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="a4d29-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="a4d29-123">Ayrıca, `FunctionLeave2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4d29-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d29-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4d29-124">Requirements</span></span>  
 <span data-ttu-id="a4d29-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d29-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d29-126">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a4d29-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a4d29-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a4d29-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4d29-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d29-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d29-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d29-129">See also</span></span>

- [<span data-ttu-id="a4d29-130">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4d29-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="a4d29-131">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4d29-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="a4d29-132">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4d29-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="a4d29-133">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a4d29-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
