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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9dee1404a8da63208bba7b7529b16eabbee3254
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745768"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="b9f92-102">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="b9f92-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="b9f92-103">Profil Oluşturucu bir işlev, verilen tanımlayıcıya için kullanılmak üzere diğer Kimliğe yeniden eşlenebileceğini bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) söz konusu işlev için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="b9f92-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="b9f92-104">`FunctionIDMapper` Ayrıca, profil oluşturucunun söz konusu işlev için geri çağırmaları almak isteyip istemediğini göstermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9f92-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9f92-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9f92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9f92-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b9f92-107">[in] Eşleştirilecek işlev tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b9f92-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="b9f92-108">[out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` geri çağırmaları; Aksi takdirde, bu değeri ayarlar `false`.</span><span class="sxs-lookup"><span data-stu-id="b9f92-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9f92-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9f92-109">Return Value</span></span>  
 <span data-ttu-id="b9f92-110">Profil Oluşturucu, yürütme altyapısı bir alternatif bir işlev tanımlayıcı olarak kullanan bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9f92-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="b9f92-111">Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="b9f92-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="b9f92-112">Aksi takdirde, null dönüş değeri, büyük olasılıkla işlem durdurma dahil, öngörülemeyen sonuçlara üretecektir.</span><span class="sxs-lookup"><span data-stu-id="b9f92-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9f92-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9f92-113">Remarks</span></span>  
 <span data-ttu-id="b9f92-114">`FunctionIDMapper` Bir geri çağırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="b9f92-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="b9f92-115">Bir işlev kimliği için profil oluşturucuyu daha yararlı olan bazı bir tanımlayıcıya yeniden eşlemek için Profil Oluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b9f92-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="b9f92-116">`FunctionIDMapper` Belirli bir işlev için kullanılacak alternatif Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9f92-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="b9f92-117">Ardından yürütme altyapısı profil geri dön geleneksel işlevi kimliği yanı sıra bu alternatif kimliği geçirerek profil oluşturucunun isteği geliştirir `clientData` parametresinin `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` kancaları tanımlamak için kanca hangi Aranan işlev.</span><span class="sxs-lookup"><span data-stu-id="b9f92-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="b9f92-118">Kullanabileceğiniz [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) uygulamasını belirtmek üzere yöntem `FunctionIDMapper` işlevi.</span><span class="sxs-lookup"><span data-stu-id="b9f92-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="b9f92-119">Çağırabilirsiniz `ICorProfilerInfo::SetFunctionIDMapper` yöntemi yalnızca bir kez ve biz öneririz, böylece bunu [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b9f92-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="b9f92-120">Varsayılan olarak, bir profil oluşturucu, COR_PRF_MONITOR_ENTERLEAVE bayrağını kullanarak ayarlar, görünür duruma varsayılır [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), ve kancaları aracılığıyla ayarlar [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [Icorprofilerınfo2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), alması gereken `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` her işlev için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="b9f92-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="b9f92-121">Ancak, profil oluşturucular uygulayabilir `FunctionIDMapper` ayarlayarak bu geri aramalarda belirli alma seçici olarak önlemek için işlevleri `pbHookFunction` için `false`.</span><span class="sxs-lookup"><span data-stu-id="b9f92-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="b9f92-122">Profil oluşturucular burada birden çok iş parçacığı profili oluşturulan bir uygulamanın aynı yöntemi/işlevi aynı anda aradığınız örneklerini dayanıklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9f92-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="b9f92-123">Böyle durumlarda, birden çok profil oluşturucu alabilirsiniz `FunctionIDMapper` geri çağırmalar için aynı `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="b9f92-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="b9f92-124">Profil Oluşturucu ile aynı birden çok kez çağrıldığında, bu geri çağrısından aynı değerleri döndürülecek belirli olmalıdır `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="b9f92-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f92-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9f92-125">Requirements</span></span>  
 <span data-ttu-id="b9f92-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9f92-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9f92-127">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b9f92-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b9f92-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9f92-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9f92-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9f92-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f92-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9f92-130">See also</span></span>

- [<span data-ttu-id="b9f92-131">SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9f92-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="b9f92-132">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="b9f92-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="b9f92-133">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="b9f92-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="b9f92-134">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="b9f92-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="b9f92-135">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="b9f92-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="b9f92-136">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b9f92-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
