---
title: FunctionIDMapper İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866950"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="d83c6-102">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="d83c6-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="d83c6-103">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="d83c6-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="d83c6-104">`FunctionIDMapper`, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d83c6-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d83c6-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d83c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d83c6-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="d83c6-107">\[içinde] yeniden eşleştirilecek işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d83c6-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="d83c6-108">\[out] profil oluşturucunun `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almak isterse `true` için ayarladığı değere yönelik bir işaretçi. Aksi takdirde, bu değeri `false`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d83c6-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d83c6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d83c6-109">Return Value</span></span>  
 <span data-ttu-id="d83c6-110">Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d83c6-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="d83c6-111">`pbHookFunction``false` döndürülmediği takdirde dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="d83c6-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="d83c6-112">Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi çok büyük olasılıkla halele vermez.</span><span class="sxs-lookup"><span data-stu-id="d83c6-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d83c6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d83c6-113">Remarks</span></span>  
 <span data-ttu-id="d83c6-114">`FunctionIDMapper` işlevi bir geri çağırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d83c6-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="d83c6-115">Bir işlev KIMLIĞINI profil Oluşturucu için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profil oluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d83c6-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="d83c6-116">`FunctionIDMapper`, verilen herhangi bir işlev için kullanılacak alternatif KIMLIĞI döndürür.</span><span class="sxs-lookup"><span data-stu-id="d83c6-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="d83c6-117">Yürütme altyapısı daha sonra, bu alternatif KIMLIĞI, geleneksel işlev KIMLIĞINE ek olarak, `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` kancalarını `clientData` parametresindeki Profiler 'a geri geçirerek, kancaın çağrıldığı işlevi belirlemek için profil oluşturucunun isteğine geçer.</span><span class="sxs-lookup"><span data-stu-id="d83c6-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="d83c6-118">`FunctionIDMapper` işlevinin uygulamasını belirtmek için [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d83c6-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="d83c6-119">`ICorProfilerInfo::SetFunctionIDMapper` yöntemini yalnızca bir kez çağırabilirsiniz ve [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırmasında bunu yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d83c6-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="d83c6-120">Varsayılan olarak, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağını ayarlayan ve [ICorProfilerInfo:: Setenterleavefunctionkancaları](icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)aracılığıyla kancaları ayarlayan bir profil oluşturucu, her işlev için `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="d83c6-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="d83c6-121">Ancak, profil oluşturucular, `false`' e `pbHookFunction` ayarlayarak belirli işlevler için bu geri çağırmaları almayı seçerek `FunctionIDMapper` uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="d83c6-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="d83c6-122">Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı anda aynı yöntemi/işlevi aldığı durumlarda toleranslı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d83c6-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="d83c6-123">Bu gibi durumlarda, profil oluşturucu aynı `FunctionID`birden çok `FunctionIDMapper` geri çağırma alabilir.</span><span class="sxs-lookup"><span data-stu-id="d83c6-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="d83c6-124">Profil Oluşturucu aynı `FunctionID`birden çok kez çağrıldığında, bu geri aramadan aynı değerleri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d83c6-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83c6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d83c6-125">Requirements</span></span>  
 <span data-ttu-id="d83c6-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83c6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83c6-127">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="d83c6-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d83c6-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d83c6-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d83c6-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83c6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83c6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d83c6-130">See also</span></span>

- [<span data-ttu-id="d83c6-131">SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d83c6-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d83c6-132">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d83c6-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="d83c6-133">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d83c6-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d83c6-134">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d83c6-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="d83c6-135">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d83c6-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="d83c6-136">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d83c6-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
