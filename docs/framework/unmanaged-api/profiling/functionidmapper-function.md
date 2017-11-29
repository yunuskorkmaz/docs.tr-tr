---
title: "FunctionIDMapper İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 629bcd5085169fcb136884c53434c29d385642cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="ab45f-102">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="ab45f-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="ab45f-103">Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) bu işlev için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="ab45f-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="ab45f-104">`FunctionIDMapper`Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab45f-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab45f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab45f-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab45f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab45f-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="ab45f-107">[in] Eşleştirilmesi için işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ab45f-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="ab45f-108">[out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa, `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` geri aramalar; Aksi takdirde, bu değeri ayarlar `false`.</span><span class="sxs-lookup"><span data-stu-id="ab45f-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab45f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab45f-109">Return Value</span></span>  
 <span data-ttu-id="ab45f-110">Profil Oluşturucu yürütme altyapısı bir alternatif işlevi tanımlayıcı olarak kullanan bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab45f-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="ab45f-111">Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="ab45f-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="ab45f-112">Aksi takdirde null dönüş değeri büyük olasılıkla işlemi durdurma dahil, öngörülemeyen sonuçlara oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab45f-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab45f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab45f-113">Remarks</span></span>  
 <span data-ttu-id="ab45f-114">`FunctionIDMapper` Bir geri çağırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="ab45f-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="ab45f-115">Profil Oluşturucu için daha yararlı olan başka bir tanımlayıcı işlevi Kimliğine yeniden eşlemek için Profil Oluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ab45f-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="ab45f-116">`FunctionIDMapper` Belirli bir işlev için kullanılacak alternatif Kimliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab45f-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="ab45f-117">Profil Oluşturucu'nın istek sonra geliştirir yanı sıra geleneksel işlevi kimliği bu alternatif kimlik geri Profil Oluşturucusu'nda geçirerek yürütme altyapısı `clientData` parametresinin `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` tanımlamak için kancaları kendisi için kanca çağrılan işlev.</span><span class="sxs-lookup"><span data-stu-id="ab45f-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="ab45f-118">Kullanabileceğiniz [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) uygulanması belirtmek için yöntemi `FunctionIDMapper` işlevi.</span><span class="sxs-lookup"><span data-stu-id="ab45f-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="ab45f-119">Çağırabilirsiniz `ICorProfilerInfo::SetFunctionIDMapper` yöntemi yalnızca bir kez ve biz öneririz, böylece bunu [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ab45f-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="ab45f-120">Varsayılan olarak, bir profil oluşturucu COR_PRF_MONITOR_ENTERLEAVE bayrağını kullanarak ayarlayan olduğunu görünür duruma varsayılır [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), ve aracılığıyla kancaları ayarlar [Icorprofilerınfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [Icorprofilerınfo2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), alması gereken `FunctionEnter2`, `FunctionLeave2`, ve `FunctionTailcall2` her işlev için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="ab45f-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="ab45f-121">Ancak, profil oluşturucular uygulayabilir `FunctionIDMapper` ayarlayarak seçerek bu geri aramalar belirli almayı önlemek için işlevleri `pbHookFunction` için `false`.</span><span class="sxs-lookup"><span data-stu-id="ab45f-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="ab45f-122">Profil oluşturucular burada profili uygulamasının birden çok iş parçacığı aynı yöntemi ya da işlevin aynı anda bulunduğunuz örneklerini dayanıklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab45f-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="ab45f-123">Böyle durumlarda, birden çok profil oluşturucu alabilirsiniz `FunctionIDMapper` geri aramalar için aynı `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="ab45f-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="ab45f-124">Profil Oluşturucu ile aynı birden çok kez çağrıldığında, bu geri aramasından aynı değerlere döndürmek emin olmalısınız `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="ab45f-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab45f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab45f-125">Requirements</span></span>  
 <span data-ttu-id="ab45f-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab45f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab45f-127">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ab45f-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ab45f-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab45f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab45f-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab45f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab45f-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab45f-130">See Also</span></span>  
 [<span data-ttu-id="ab45f-131">Setfunctionıdmapper yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab45f-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="ab45f-132">Functionıdmapper2 işlevi</span><span class="sxs-lookup"><span data-stu-id="ab45f-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="ab45f-133">FunctionEnter2 işlevi</span><span class="sxs-lookup"><span data-stu-id="ab45f-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="ab45f-134">FunctionLeave2 işlevi</span><span class="sxs-lookup"><span data-stu-id="ab45f-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="ab45f-135">FunctionTailcall2 işlevi</span><span class="sxs-lookup"><span data-stu-id="ab45f-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="ab45f-136">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="ab45f-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
