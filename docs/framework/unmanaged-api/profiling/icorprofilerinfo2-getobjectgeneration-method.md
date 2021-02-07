---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: GetObjectGeneration yöntemi'
title: ICorProfilerInfo2::GetObjectGeneration Yöntemi
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
ms.openlocfilehash: f4927c081393a11f7dad7d59cce311b82072659c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716451"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="e2aeb-103">ICorProfilerInfo2::GetObjectGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2aeb-103">ICorProfilerInfo2::GetObjectGeneration Method</span></span>

<span data-ttu-id="e2aeb-104">Belirtilen nesneyi içeren yığının segmentini alır.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-104">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2aeb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2aeb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2aeb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2aeb-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="e2aeb-107">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-107">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="e2aeb-108">dışı Atık toplama yapılmakta olan neslin içindeki bir bellek aralığını (yani bir blok) açıklayan [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-108">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="e2aeb-109">Bu Aralık belirtilen nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-109">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2aeb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2aeb-110">Remarks</span></span>  

 <span data-ttu-id="e2aeb-111">`GetObjectGeneration`Çöp toplama işlemi devam ettiğinden, yöntemi herhangi bir profil oluşturucu geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-111">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="e2aeb-112">Diğer bir deyişle, [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ve [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)arasında gerçekleşenler hariç herhangi bir geri aramadan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-112">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2aeb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2aeb-113">Requirements</span></span>  

 <span data-ttu-id="e2aeb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2aeb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2aeb-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2aeb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2aeb-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2aeb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2aeb-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2aeb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2aeb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2aeb-118">See also</span></span>

- [<span data-ttu-id="e2aeb-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2aeb-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e2aeb-120">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2aeb-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
