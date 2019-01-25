---
title: ICorProfilerInfo2::GetObjectGeneration Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dcc7770f95c0cb7d416480145a430d781e093f6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599679"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="d8f85-102">ICorProfilerInfo2::GetObjectGeneration Metodu</span><span class="sxs-lookup"><span data-stu-id="d8f85-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="d8f85-103">Belirtilen nesneyi içeren yığın kesimini alır.</span><span class="sxs-lookup"><span data-stu-id="d8f85-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8f85-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8f85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8f85-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d8f85-106">[in] Nesnenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="d8f85-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="d8f85-107">[out] Bir işaretçi bir [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı, bellek çeşitli (diğer bir deyişle, bir blok) içinde çöp toplama aşamasında oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8f85-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="d8f85-108">Bu aralık, belirtilen nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="d8f85-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8f85-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8f85-109">Remarks</span></span>  
 <span data-ttu-id="d8f85-110">`GetObjectGeneration` Yöntemi çağrılabilir herhangi bir profil oluşturucu geri çağrısından koşuluyla atık toplama devam ederken değil.</span><span class="sxs-lookup"><span data-stu-id="d8f85-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="d8f85-111">Diğer bir deyişle, herhangi bir geri çağırma arasında gerçekleşen hariç çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8f85-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f85-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8f85-112">Requirements</span></span>  
 <span data-ttu-id="d8f85-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8f85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f85-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8f85-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8f85-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8f85-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8f85-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f85-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f85-117">See also</span></span>
- [<span data-ttu-id="d8f85-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8f85-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d8f85-119">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8f85-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
