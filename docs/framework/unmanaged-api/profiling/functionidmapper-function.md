---
description: ': FunctionIDMapper Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 2db616509bf5dcb5b8aee9cea76a9841369ec49d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759260"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="cca1e-103">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="cca1e-103">FunctionIDMapper Function</span></span>

<span data-ttu-id="cca1e-104">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cca1e-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="cca1e-105">`FunctionIDMapper` Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cca1e-105">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca1e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cca1e-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cca1e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cca1e-107">Parameters</span></span>

<span data-ttu-id="cca1e-108">`funcId` 'ndaki Yeniden eşleştirilecek işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cca1e-108">`funcId` [in] The function identifier to be remapped.</span></span>

<span data-ttu-id="cca1e-109">`pbHookFunction` dışı Profil oluşturucunun `true` ,, ve geri çağırmaları almak istiyorsa bir değere işaretçi `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` ; Aksi takdirde, bu değeri olarak ayarlar `false` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-109">`pbHookFunction` [out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="cca1e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cca1e-110">Return Value</span></span>  

 <span data-ttu-id="cca1e-111">Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="cca1e-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="cca1e-112">Dönüş değeri, `false` içinde döndürülmediği takdirde null olamaz `pbHookFunction` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="cca1e-113">Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi çok büyük olasılıkla halele vermez.</span><span class="sxs-lookup"><span data-stu-id="cca1e-113">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cca1e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cca1e-114">Remarks</span></span>  

 <span data-ttu-id="cca1e-115">`FunctionIDMapper`İşlev bir geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="cca1e-115">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="cca1e-116">Bir işlev KIMLIĞINI profil Oluşturucu için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profil oluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cca1e-116">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="cca1e-117">, `FunctionIDMapper` Verilen herhangi bir işlev için kullanılacak ALTERNATIF kimliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="cca1e-117">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="cca1e-118">Yürütme altyapısı daha sonra bu alternatif KIMLIĞI geçirerek (geleneksel işlev KIMLIĞINE ek olarak,, `clientData` `FunctionEnter2` `FunctionLeave2` , ve `FunctionTailcall2` kancalarının çağrıldığı işlevi belirlemek için),, ve kancalarının parametresindeki profil oluşturucuya geri dönerek profil oluşturucunun isteğine geçer.</span><span class="sxs-lookup"><span data-stu-id="cca1e-118">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="cca1e-119">İşlevin uygulamasını belirtmek için [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz `FunctionIDMapper` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-119">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="cca1e-120">`ICorProfilerInfo::SetFunctionIDMapper`Yöntemi yalnızca bir kez çağırabilir ve [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırmasında bunu yapmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="cca1e-120">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="cca1e-121">Varsayılan olarak, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağını ayarlayan ve [ICorProfilerInfo:: Setenterleavefunctionkancaları](icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)aracılığıyla kancaları ayarlayan bir profil oluşturucu, `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` her işlev için, ve geri çağırmaları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="cca1e-121">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="cca1e-122">Ancak, profil oluşturucular ' `FunctionIDMapper` ye ayarlayarak belirli işlevler için bu geri çağırmaları, seçmeli olarak almak için uygulanabilir `pbHookFunction` `false` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-122">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="cca1e-123">Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı anda aynı yöntemi/işlevi aldığı durumlarda toleranslı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cca1e-123">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="cca1e-124">Bu gibi durumlarda, profil oluşturucu `FunctionIDMapper` aynı için birden fazla geri çağırma alabilir `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-124">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="cca1e-125">Profil Oluşturucu aynı değeri aynı değer ile birden çok kez çağrıldığında, bu geri aramadan aynı değerleri döndürmelidir `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="cca1e-125">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cca1e-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cca1e-126">Requirements</span></span>  

 <span data-ttu-id="cca1e-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cca1e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cca1e-128">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="cca1e-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="cca1e-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cca1e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cca1e-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cca1e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca1e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cca1e-131">See also</span></span>

- [<span data-ttu-id="cca1e-132">SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cca1e-132">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="cca1e-133">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cca1e-133">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="cca1e-134">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cca1e-134">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="cca1e-135">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cca1e-135">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="cca1e-136">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cca1e-136">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="cca1e-137">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cca1e-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
