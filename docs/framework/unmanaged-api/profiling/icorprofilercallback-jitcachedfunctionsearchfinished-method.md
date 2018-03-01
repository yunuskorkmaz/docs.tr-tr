---
title: "ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 830d790426dd53de100784f585a6733e278a9569
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="9aafb-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aafb-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="9aafb-103">Profil Oluşturucu, arama yerel Görüntü Oluşturucu (NGen.exe) kullanarak önceden derlenen bir işlev için tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="9aafb-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aafb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9aafb-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9aafb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9aafb-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9aafb-106">[in] Arama gerçekleştirilip gerçekleştirilmediğine işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="9aafb-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="9aafb-107">[in] Değerini [cor_prf_jıt_cache](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) arama sonucu gösterir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="9aafb-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aafb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aafb-108">Remarks</span></span>  
 <span data-ttu-id="9aafb-109">.NET Framework sürüm 2.0, [Icorprofilercallback::jıtcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri aramalar değil oluşturulacak normal NGen görüntüleri uygulamasında tüm işlevleri için.</span><span class="sxs-lookup"><span data-stu-id="9aafb-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="9aafb-110">Yalnızca bir profil oluşturucu için en iyi duruma getirilmiş NGen görüntüleri tüm işlevleri için geri çağırmaları görüntüde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9aafb-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="9aafb-111">Yalnızca bir işlevin derlenmiş tam zamanında (JIT) olmasını zorlamak için bu geri aramalar kullanmaya çalışırsa, ancak ek yükü nedeniyle, bir profil oluşturucu profil oluşturucu en iyileştirilmiş NGen görseller istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aafb-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="9aafb-112">Aksi takdirde, profil oluşturucu işlevi bilgilerini toplamak için yavaş bir strateji kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aafb-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aafb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9aafb-113">Requirements</span></span>  
 <span data-ttu-id="9aafb-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aafb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aafb-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9aafb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9aafb-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9aafb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aafb-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aafb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aafb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aafb-118">See Also</span></span>  
 [<span data-ttu-id="9aafb-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aafb-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
