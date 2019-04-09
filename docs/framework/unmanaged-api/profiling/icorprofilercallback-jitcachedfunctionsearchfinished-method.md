---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122947"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="b892b-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b892b-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="b892b-103">Profil Oluşturucu, arama Native Image Generator (NGen.exe) kullanarak önceden derlenen bir işlev için tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b892b-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b892b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b892b-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b892b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b892b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b892b-106">[in] Aramanın gerçekleştirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="b892b-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="b892b-107">[in] Değerini [cor_prf_jıt_cache](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) arama sonucunu gösteren sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b892b-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b892b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b892b-108">Remarks</span></span>  
 <span data-ttu-id="b892b-109">.NET Framework sürüm 2.0 [Icorprofilercallback::jıtcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri çağırmaları değil oluşturulacak normal NGen görüntülerinin tüm işlevler için.</span><span class="sxs-lookup"><span data-stu-id="b892b-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="b892b-110">Yalnızca bir profil oluşturucu için en iyi duruma getirilmiş NGen görüntülerinin geri çağırmaları tüm işlevler görüntüde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b892b-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="b892b-111">Ancak, yalnızca derlenmiş just-in-time (JIT) gereken işlevi zorlamak için bu geri aramalarda kullanmaya çalışırsa, ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu için iyileştirilmiş NGen görüntülerinin istemelidir.</span><span class="sxs-lookup"><span data-stu-id="b892b-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="b892b-112">Aksi takdirde, profil oluşturucu işlevi bilgileri toplamak için yavaş bir strateji kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b892b-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b892b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b892b-113">Requirements</span></span>  
 <span data-ttu-id="b892b-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b892b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b892b-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b892b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b892b-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b892b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b892b-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b892b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b892b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b892b-118">See also</span></span>

- [<span data-ttu-id="b892b-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b892b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
