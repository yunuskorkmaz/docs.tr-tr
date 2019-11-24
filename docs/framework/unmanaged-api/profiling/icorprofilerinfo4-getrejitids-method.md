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
ms.openlocfilehash: f6d26abba649b608858fde8beaac750600493869
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442860"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="3c170-102">ICorProfilerInfo4::GetReJITIDs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c170-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="3c170-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span><span class="sxs-lookup"><span data-stu-id="3c170-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="3c170-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span><span class="sxs-lookup"><span data-stu-id="3c170-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c170-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c170-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c170-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c170-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3c170-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span><span class="sxs-lookup"><span data-stu-id="3c170-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="3c170-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span><span class="sxs-lookup"><span data-stu-id="3c170-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="3c170-109">[out] The actual number of JIT-recompiled IDs.</span><span class="sxs-lookup"><span data-stu-id="3c170-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="3c170-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span><span class="sxs-lookup"><span data-stu-id="3c170-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c170-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c170-111">Remarks</span></span>  
 <span data-ttu-id="3c170-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span><span class="sxs-lookup"><span data-stu-id="3c170-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="3c170-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span><span class="sxs-lookup"><span data-stu-id="3c170-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c170-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c170-114">Requirements</span></span>  
 <span data-ttu-id="3c170-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c170-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c170-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c170-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c170-117">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c170-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c170-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c170-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c170-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c170-119">See also</span></span>

- [<span data-ttu-id="3c170-120">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c170-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="3c170-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c170-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3c170-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c170-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
