---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2208a1a1637b3bb8dd7d7963ab806aeae7921dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="96b21-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96b21-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="96b21-103">Profil Oluşturucu, arama yerel Görüntü Oluşturucu (NGen.exe) kullanarak önceden derlenen bir işlev için başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="96b21-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96b21-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96b21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96b21-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="96b21-106">[in] Arama gerçekleştirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="96b21-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="96b21-107">[out] `true` yürütme altyapısı, (varsa) bir işlev önbelleğe alınmış sürümünü kullanmanız gerekir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="96b21-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="96b21-108">Değer ise `false`, yürütme altyapısı JIT derlerken JIT derlenmiş olmayan bir sürüm kullanmak yerine işlevi.</span><span class="sxs-lookup"><span data-stu-id="96b21-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b21-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96b21-109">Remarks</span></span>  
 <span data-ttu-id="96b21-110">.NET Framework sürüm 2.0, `JITCachedFunctionSearchStarted` ve [Icorprofilercallback::jıtcachedfunctionsearchfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) geri aramalar değil oluşturulacak normal NGen görüntüleri uygulamasında tüm işlevleri için.</span><span class="sxs-lookup"><span data-stu-id="96b21-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="96b21-111">Yalnızca bir profil için en iyi duruma getirilmiş NGen görüntüleri tüm işlevleri için geri çağırmaları görüntüde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96b21-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="96b21-112">Yalnızca bir işlevin derlenmiş tam zamanında (JIT) olmasını zorlamak için bu geri aramalar kullanmaya çalışırsa, ancak ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu en iyileştirilmiş NGen görseller istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96b21-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="96b21-113">Aksi takdirde, profil oluşturucu işlevi bilgilerini toplamak için yavaş bir strateji kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96b21-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="96b21-114">Profil oluşturucular burada profili uygulamasının birden çok iş parçacığı aynı yöntemi aynı anda aramakta olduğunuz durumlarda desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="96b21-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="96b21-115">Örneğin, iş parçacığı A çağırır `JITCachedFunctionSearchStarted` ve profil oluşturucu ayarlayarak yanıt verdiğini *pbUseCachedFunction*JIT derleme zorlamak için false.</span><span class="sxs-lookup"><span data-stu-id="96b21-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="96b21-116">Sonra A çağıran iş parçacığı [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="96b21-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="96b21-117">Şimdi B çağrıları iş parçacığı `JITCachedFunctionSearchStarted` aynı işlevi için.</span><span class="sxs-lookup"><span data-stu-id="96b21-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="96b21-118">Profil Oluşturucu Niyet JIT derleme işlevi için belirtilen olsa bile, iş parçacığı A'ın çağrısı için profil oluşturucu yanıtladı önce iş parçacığı B geri gönderdiği için profil oluşturucu ikinci geri çağırma alır `JITCachedFunctionSearchStarted`.</span><span class="sxs-lookup"><span data-stu-id="96b21-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="96b21-119">İş parçacıklarını nasıl zamanlanmış iş parçacıklarının çağrıları yapma sırası bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="96b21-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="96b21-120">Profil Oluşturucu yinelenen geri aramalar aldığında, tarafından başvurulan değer ayarlamalısınız `pbUseCachedFunction` tüm yinelenen geri aramalar için aynı değeri için.</span><span class="sxs-lookup"><span data-stu-id="96b21-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="96b21-121">Diğer bir deyişle, ne zaman `JITCachedFunctionSearchStarted` birden çok kez aynı adlı `functionId` değeri, profil oluşturucu her zaman aynı yanıtlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96b21-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b21-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96b21-122">Requirements</span></span>  
 <span data-ttu-id="96b21-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b21-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b21-124">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96b21-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96b21-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96b21-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96b21-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b21-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b21-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96b21-127">See Also</span></span>  
 [<span data-ttu-id="96b21-128">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96b21-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
