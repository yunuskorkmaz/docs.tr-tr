---
title: ICorProfilerInfo4::GetReJITIDs Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="bb20a-102">ICorProfilerInfo4::GetReJITIDs Metodu</span><span class="sxs-lookup"><span data-stu-id="bb20a-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="bb20a-103">Hala ayrılan tüm JIT yeniden derlenmesi sürümlerini belirtilen işlev tanımlamak kimlikleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb20a-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="bb20a-104">Bu, daha sonra geri döndürüldü, ancak (örneğin, geri döndürülen işlevi içeren uygulama etki alanı hala kullanımda olduğunda) henüz serbest işlevleri JIT yeniden derlenmesi sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bb20a-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb20a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb20a-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb20a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb20a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bb20a-107">[in] `FunctionID` Olan sürümler Numaralandırılacak işlevi örneğinin.</span><span class="sxs-lookup"><span data-stu-id="bb20a-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="bb20a-108">[in] JIT yeniden derlenmesi kimlikleri ayrılan sayısı `reJitIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="bb20a-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="bb20a-109">[out] JIT yeniden derlenmesi kimlikleri gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="bb20a-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="bb20a-110">[out] Belirtilen işlev için JIT yeniden derlenmesi kimlikleri içerecek bir çağıran tarafından ayrılmış bir dizi.</span><span class="sxs-lookup"><span data-stu-id="bb20a-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb20a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb20a-111">Remarks</span></span>  
 <span data-ttu-id="bb20a-112">`GetReJITIDs`verilen işlevin örneği için etkin JIT yeniden derlenmesi kimlikleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bb20a-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="bb20a-113">Diğer aynı kullanım deseni takip `ICorProfilerInfo` arayana ayrılan arabellekleri kabul işlevleri.</span><span class="sxs-lookup"><span data-stu-id="bb20a-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb20a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb20a-114">Requirements</span></span>  
 <span data-ttu-id="bb20a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb20a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb20a-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb20a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb20a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb20a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb20a-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb20a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb20a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb20a-119">See Also</span></span>  
 [<span data-ttu-id="bb20a-120">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb20a-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="bb20a-121">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb20a-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bb20a-122">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb20a-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
