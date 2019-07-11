---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d35179b8ae35c03370cc3798609d6ed430cde3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782847"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="c172d-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c172d-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="c172d-103">Profil Oluşturucu, arama Native Image Generator (NGen.exe) kullanarak önceden derlenen bir işlev için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c172d-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c172d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c172d-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c172d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c172d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c172d-106">[in] Aramanın gerçekleştirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="c172d-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="c172d-107">[out] `true` yürütme altyapısı, (varsa) bir işlev önbelleğe alınmış sürümünü kullanmanız gerekir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="c172d-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="c172d-108">Değer ise `false`, JIT olarak derlenmiş değil bir sürümünü kullanmak yerine, işlevi yürütme altyapısı JIT derlenir.</span><span class="sxs-lookup"><span data-stu-id="c172d-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c172d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c172d-109">Remarks</span></span>  
 <span data-ttu-id="c172d-110">.NET Framework sürüm 2.0 `JITCachedFunctionSearchStarted` ve [Icorprofilercallback::jıtcachedfunctionsearchfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları değil oluşturulacak normal NGen görüntülerinin tüm işlevler için.</span><span class="sxs-lookup"><span data-stu-id="c172d-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="c172d-111">Bir profil için en iyi duruma getirilmiş NGen görüntülerinin geri çağırmaları tüm işlevler görüntüde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c172d-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="c172d-112">Ancak, yalnızca derlenmiş just-in-time (JIT) gereken işlevi zorlamak için bu geri aramalarda kullanmaya çalışırsa, ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu için iyileştirilmiş NGen görüntülerinin istemelidir.</span><span class="sxs-lookup"><span data-stu-id="c172d-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="c172d-113">Aksi takdirde, profil oluşturucu işlevi bilgileri toplamak için yavaş bir strateji kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c172d-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="c172d-114">Profil Oluşturucular, burada, profili oluşturulmuş bir uygulama birden çok iş parçacığı aynı yöntemi aynı anda aradığınız çalışmaları desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c172d-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="c172d-115">Örneğin, bir iş parçacığı çağrı `JITCachedFunctionSearchStarted` ve profil oluşturucu ayarlayarak yanıt *pbUseCachedFunction*JIT derlemesi zorlamak için false.</span><span class="sxs-lookup"><span data-stu-id="c172d-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="c172d-116">Bir daha sonra çağıran iş parçacığı [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="c172d-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="c172d-117">Artık B çağrılar iş parçacığı `JITCachedFunctionSearchStarted` aynı işlevi.</span><span class="sxs-lookup"><span data-stu-id="c172d-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="c172d-118">Profil Oluşturucu Niyet JIT derleme işlevi için belirtilen olsa da, profil oluşturucu için iş parçacığı A çağrısına yanıtladı önce geri çağırma iş parçacığı B gönderdiği için profil oluşturucu ikinci geri çağırma alır `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="c172d-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="c172d-119">İş parçacıklarını nasıl zamanlanmış iş parçacıklarını çağrı nasıl siparişe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c172d-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="c172d-120">Profil oluşturucuyu yinelenen geri çağırmaları aldığında tarafından başvurulan değer ayarlamalısınız `pbUseCachedFunction` için yinelenen tüm geri çağırmalar için aynı değeri.</span><span class="sxs-lookup"><span data-stu-id="c172d-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="c172d-121">Diğer bir deyişle, `JITCachedFunctionSearchStarted` birden çok kez aynı adlı `functionId` değeri, profil oluşturucu her zaman aynı yanıt vermelidir.</span><span class="sxs-lookup"><span data-stu-id="c172d-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c172d-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c172d-122">Requirements</span></span>  
 <span data-ttu-id="c172d-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c172d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c172d-124">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c172d-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c172d-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c172d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c172d-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c172d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c172d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c172d-127">See also</span></span>

- [<span data-ttu-id="c172d-128">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c172d-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
