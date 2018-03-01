---
title: ICorProfilerInfo2::GetObjectGeneration Metodu
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
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7a28b5e031ae39be39cc00740043b86ef2a9854
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="161b0-102">ICorProfilerInfo2::GetObjectGeneration Metodu</span><span class="sxs-lookup"><span data-stu-id="161b0-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="161b0-103">Belirtilen nesne içeren öbek kesimini alır.</span><span class="sxs-lookup"><span data-stu-id="161b0-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="161b0-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="161b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="161b0-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="161b0-106">[in] Nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="161b0-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="161b0-107">[out] Bir işaretçi bir [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) çöp toplama yapılıyor nesil içinde çeşitli (diğer bir deyişle, bir blok) bellek açıklar yapısı.</span><span class="sxs-lookup"><span data-stu-id="161b0-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="161b0-108">Bu aralık, belirtilen nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="161b0-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="161b0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="161b0-109">Remarks</span></span>  
 <span data-ttu-id="161b0-110">`GetObjectGeneration` Yöntemi çağrılabilir tüm profil oluşturucu geri aramasından koşuluyla çöp toplama değildir.</span><span class="sxs-lookup"><span data-stu-id="161b0-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="161b0-111">Diğer bir deyişle, onu arasında oluşan olanlar dışında herhangi bir geri çağırma çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="161b0-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161b0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="161b0-112">Requirements</span></span>  
 <span data-ttu-id="161b0-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161b0-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="161b0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="161b0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="161b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="161b0-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161b0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="161b0-117">See Also</span></span>  
 [<span data-ttu-id="161b0-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="161b0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="161b0-119">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="161b0-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
