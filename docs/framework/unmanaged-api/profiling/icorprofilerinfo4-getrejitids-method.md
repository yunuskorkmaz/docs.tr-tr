---
title: ICorProfilerInfo4::GetReJITIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2d48e5fb070ec0334de579d2e28146177a87b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049485"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="98c27-102">ICorProfilerInfo4::GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98c27-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="98c27-103">Yine de atanan tüm JIT yeniden derlenen sürümlerini belirtilen işlev tanımlamak kimlikleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="98c27-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="98c27-104">Bu, daha sonra geri döndürüldü, ancak (örneğin, geri döndürülen işlevi içeren uygulama etki alanı hala kullanımda olduğunda) henüz serbest işlevlerin JIT yeniden derlenen sürümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="98c27-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98c27-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98c27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98c27-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="98c27-107">[in] `FunctionID` Hangi sürümleri Numaralandırılacak işlevi örneği.</span><span class="sxs-lookup"><span data-stu-id="98c27-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="98c27-108">[in] JIT yeniden derlenen kimlikleri ayrıldığı sayısı `reJitIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="98c27-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="98c27-109">[out] JIT yeniden derlenen kimlikleri gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="98c27-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="98c27-110">[out] Belirtilen işlev için JIT yeniden derlenen kimlikleri içeren bir arayan tarafından ayrılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="98c27-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98c27-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98c27-111">Remarks</span></span>  
 <span data-ttu-id="98c27-112">`GetReJITIDs` verilen işlevin örneği için etkin JIT yeniden derlenen kimlikleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="98c27-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="98c27-113">Diğer olarak aynı kullanım deseni izler `ICorProfilerInfo` arayana ayrılan arabellekler kabul işlevleri.</span><span class="sxs-lookup"><span data-stu-id="98c27-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98c27-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98c27-114">Requirements</span></span>  
 <span data-ttu-id="98c27-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98c27-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c27-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98c27-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98c27-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98c27-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98c27-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c27-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c27-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98c27-119">See also</span></span>

- [<span data-ttu-id="98c27-120">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98c27-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="98c27-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98c27-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="98c27-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="98c27-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
