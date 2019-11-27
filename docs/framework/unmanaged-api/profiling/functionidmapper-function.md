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
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440696"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="f60cc-102">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="f60cc-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="f60cc-103">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="f60cc-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="f60cc-104">`FunctionIDMapper`, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f60cc-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f60cc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f60cc-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f60cc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f60cc-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f60cc-107">'ndaki Yeniden eşleştirilecek işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f60cc-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="f60cc-108">dışı Profil oluşturucunun `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almak istiyorsa `true` için ayarladığı değere yönelik bir işaretçi; Aksi takdirde, bu değeri `false`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f60cc-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f60cc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f60cc-109">Return Value</span></span>  
 <span data-ttu-id="f60cc-110">Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f60cc-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="f60cc-111">`pbHookFunction``false` döndürülmediği takdirde dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="f60cc-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="f60cc-112">Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi çok büyük olasılıkla halele vermez.</span><span class="sxs-lookup"><span data-stu-id="f60cc-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f60cc-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f60cc-113">Remarks</span></span>  
 <span data-ttu-id="f60cc-114">`FunctionIDMapper` işlevi bir geri çağırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f60cc-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="f60cc-115">Bir işlev KIMLIĞINI profil Oluşturucu için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profil oluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f60cc-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="f60cc-116">`FunctionIDMapper`, verilen herhangi bir işlev için kullanılacak alternatif KIMLIĞI döndürür.</span><span class="sxs-lookup"><span data-stu-id="f60cc-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="f60cc-117">Yürütme altyapısı daha sonra, bu alternatif KIMLIĞI, geleneksel işlev KIMLIĞINE ek olarak, `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` kancalarını `clientData` parametresindeki Profiler 'a geri geçirerek, kancaın çağrıldığı işlevi belirlemek için profil oluşturucunun isteğine geçer.</span><span class="sxs-lookup"><span data-stu-id="f60cc-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="f60cc-118">`FunctionIDMapper` işlevinin uygulamasını belirtmek için [ICorProfilerInfo:: SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f60cc-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="f60cc-119">`ICorProfilerInfo::SetFunctionIDMapper` yöntemini yalnızca bir kez çağırabilirsiniz ve [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırmasında bunu yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f60cc-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="f60cc-120">Varsayılan olarak, [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağını ayarlayan ve [ICorProfilerInfo:: Setenterleavefunctionkancaları](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)aracılığıyla kancaları ayarlayan bir profil oluşturucu, her işlev için `FunctionEnter2`, `FunctionLeave2`ve `FunctionTailcall2` geri çağırmaları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f60cc-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="f60cc-121">Ancak, profil oluşturucular, `false`' e `pbHookFunction` ayarlayarak belirli işlevler için bu geri çağırmaları almayı seçerek `FunctionIDMapper` uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f60cc-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="f60cc-122">Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı anda aynı yöntemi/işlevi aldığı durumlarda toleranslı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f60cc-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="f60cc-123">Bu gibi durumlarda, profil oluşturucu aynı `FunctionID`birden çok `FunctionIDMapper` geri çağırma alabilir.</span><span class="sxs-lookup"><span data-stu-id="f60cc-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="f60cc-124">Profil Oluşturucu aynı `FunctionID`birden çok kez çağrıldığında, bu geri aramadan aynı değerleri döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f60cc-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f60cc-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f60cc-125">Requirements</span></span>  
 <span data-ttu-id="f60cc-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f60cc-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f60cc-127">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="f60cc-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f60cc-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f60cc-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f60cc-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f60cc-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60cc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f60cc-130">See also</span></span>

- [<span data-ttu-id="f60cc-131">SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f60cc-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f60cc-132">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f60cc-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="f60cc-133">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f60cc-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="f60cc-134">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f60cc-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="f60cc-135">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f60cc-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="f60cc-136">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f60cc-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
