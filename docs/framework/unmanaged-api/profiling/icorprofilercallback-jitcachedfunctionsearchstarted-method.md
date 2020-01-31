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
ms.openlocfilehash: 964ea11b8e8c8f494066249f7da2057970d7e8f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866266"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="d3108-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3108-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="d3108-103">Profil oluşturucuyu, önceden yerel görüntü Oluşturucu (NGen. exe) kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3108-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3108-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3108-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3108-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3108-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="d3108-106">\[içinde] aramanın gerçekleştirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d3108-106">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="d3108-107">\[out], yürütme altyapısının bir işlevin önbelleğe alınmış sürümünü (varsa) kullanması gerekiyorsa `true`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="d3108-107">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="d3108-108">Değer `false`ise, yürütme motoru JıT-derlenen bir sürümü kullanmak yerine, işlevi derler.</span><span class="sxs-lookup"><span data-stu-id="d3108-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3108-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3108-109">Remarks</span></span>  
 <span data-ttu-id="d3108-110">.NET Framework sürüm 2,0 ' de, normal NGen görüntülerinde tüm işlevler için `JITCachedFunctionSearchStarted` ve [ICorProfilerCallback:: JITCachedFunctionSearchFinished Yöntem](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri çağırmaları yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="d3108-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="d3108-111">Yalnızca bir profil için iyileştirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="d3108-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="d3108-112">Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir.</span><span class="sxs-lookup"><span data-stu-id="d3108-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="d3108-113">Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3108-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="d3108-114">Profil oluşturucular, profili oluşturulmuş bir uygulamanın birden çok iş parçacığının aynı yöntemi eşzamanlı olarak çağıran durumları desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="d3108-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="d3108-115">Örneğin, bir çağrı `JITCachedFunctionSearchStarted` iş parçacığı ve profil oluşturucu, JıT derlemesini zorlamak için *pbUseCachedFunction*değerini false olarak ayarlayarak yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d3108-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="d3108-116">Sonra bir A iş parçacığı [ICorProfilerCallback:: JCOR, Started](icorprofilercallback-jitcompilationstarted-method.md) ve [ICorProfilerCallback:: JCOR, finished işlemini](icorprofilercallback-jitcompilationfinished-method.md)çağırır.</span><span class="sxs-lookup"><span data-stu-id="d3108-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="d3108-117">Şimdi iş parçacığı B aynı işlev için `JITCachedFunctionSearchStarted` çağırır.</span><span class="sxs-lookup"><span data-stu-id="d3108-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="d3108-118">Profil Oluşturucu, işlevi JıT-Derle öğesine belirtse de, profil oluşturucu ikinci geri aramayı alır çünkü bu, {1} iş parçacığı, Oluşturucu A 'nın `JITCachedFunctionSearchStarted`çağrısına yanıt vermeden önce geri çağırma işlemini gönderir.</span><span class="sxs-lookup"><span data-stu-id="d3108-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="d3108-119">İş parçacıklarının çağrı yaptığı sıra, iş parçacıklarının nasıl zamanlandığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3108-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="d3108-120">Profil Oluşturucu yinelenen geri çağrılar aldığında, `pbUseCachedFunction` tarafından başvurulan değeri tüm yinelenen geri çağırmalar için aynı değere ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3108-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="d3108-121">Diğer bir deyişle, `JITCachedFunctionSearchStarted` aynı `functionId` değeri ile birden çok kez çağrıldığında, profil oluşturucunun her seferinde aynı yanıt vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3108-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3108-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3108-122">Requirements</span></span>  
 <span data-ttu-id="d3108-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3108-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3108-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d3108-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3108-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3108-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3108-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3108-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3108-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3108-127">See also</span></span>

- [<span data-ttu-id="d3108-128">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3108-128">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
