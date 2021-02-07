---
description: ': ICorProfilerCallback:: JITCachedFunctionSearchStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1faaf8fbc1e0fee9ce76850cfedcd4e8cf934371
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705778"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="8528e-103">ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8528e-103">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>

<span data-ttu-id="8528e-104">Profil oluşturucuyu, önceden yerel görüntü Oluşturucu (NGen.exe) kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="8528e-104">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8528e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8528e-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8528e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8528e-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8528e-107">\[' de] aramanın gerçekleştirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8528e-107">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="8528e-108">\[out] `true` yürütme altyapısının bir işlevin önbelleğe alınmış sürümünü kullanması gerekiyorsa (varsa); Aksi takdirde `false` .</span><span class="sxs-lookup"><span data-stu-id="8528e-108">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="8528e-109">Değer ise `false` , yürütme ALTYAPıSı JIT-derlenmiş olmayan bir sürümü kullanmak yerine, işlevi derler.</span><span class="sxs-lookup"><span data-stu-id="8528e-109">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="8528e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8528e-110">Remarks</span></span>  

 <span data-ttu-id="8528e-111">.NET Framework sürüm 2,0 ' de, `JITCachedFunctionSearchStarted` ve [ICorProfilerCallback:: JITCachedFunctionSearchFinished Yöntem](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları normal Ngen görüntülerinde tüm işlevler için yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="8528e-111">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="8528e-112">Yalnızca bir profil için iyileştirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="8528e-112">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="8528e-113">Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir.</span><span class="sxs-lookup"><span data-stu-id="8528e-113">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="8528e-114">Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8528e-114">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="8528e-115">Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı yöntemi eşzamanlı olarak çağıran durumları desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="8528e-115">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="8528e-116">Örneğin, bir çağrı iş parçacığı `JITCachedFunctionSearchStarted` ve profil oluşturucu, JIT derlemesini zorlamak Için *pbUseCachedFunction* değerini false olarak ayarlayarak yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="8528e-116">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction* to FALSE to force JIT compilation.</span></span> <span data-ttu-id="8528e-117">Sonra bir A iş parçacığı [ICorProfilerCallback:: JCOR, Started](icorprofilercallback-jitcompilationstarted-method.md) ve [ICorProfilerCallback:: JCOR, finished işlemini](icorprofilercallback-jitcompilationfinished-method.md)çağırır.</span><span class="sxs-lookup"><span data-stu-id="8528e-117">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="8528e-118">Şimdi aynı işlevi için iş parçacığı B çağrıları `JITCachedFunctionSearchStarted` .</span><span class="sxs-lookup"><span data-stu-id="8528e-118">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="8528e-119">Profil Oluşturucu, işlevi JıT-Derle öğesine belirtse de, profil oluşturucu ikinci geri aramayı alır çünkü bu, {1} iş parçacığı, ' A iş parçacığı A 'nın çağrısına yanıt vermeden önce geri çağırma işlemini gönderir `JITCachedFunctionSearchStarted` .</span><span class="sxs-lookup"><span data-stu-id="8528e-119">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="8528e-120">İş parçacıklarının çağrı yaptığı sıra, iş parçacıklarının nasıl zamanlandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8528e-120">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="8528e-121">Profil Oluşturucu yinelenen geri çağrılar aldığında, başvurulan değeri `pbUseCachedFunction` tüm yinelenen geri çağırmalar için aynı değere ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8528e-121">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="8528e-122">Diğer bir deyişle, `JITCachedFunctionSearchStarted` aynı değer ile birden çok kez çağrıldığında `functionId` , profil oluşturucunun her seferinde aynı yanıt vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8528e-122">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8528e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8528e-123">Requirements</span></span>  

 <span data-ttu-id="8528e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8528e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8528e-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8528e-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8528e-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8528e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8528e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8528e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8528e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8528e-128">See also</span></span>

- [<span data-ttu-id="8528e-129">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8528e-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
