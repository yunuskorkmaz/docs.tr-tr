---
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
ms.openlocfilehash: b75de955e3b6857c9cc1b5411df4b0f262c4cb9a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862704"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="0693c-102">ICorProfilerInfo2::GetObjectGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0693c-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="0693c-103">Belirtilen nesneyi içeren yığının segmentini alır.</span><span class="sxs-lookup"><span data-stu-id="0693c-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0693c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0693c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0693c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0693c-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="0693c-106">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0693c-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="0693c-107">dışı Atık toplama yapılmakta olan neslin içindeki bir bellek aralığını (yani bir blok) açıklayan [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0693c-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="0693c-108">Bu Aralık belirtilen nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0693c-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0693c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0693c-109">Remarks</span></span>  
 <span data-ttu-id="0693c-110">Çöp toplama işlemi devam ettiğinden, `GetObjectGeneration` yöntemi herhangi bir profil oluşturucu geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0693c-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="0693c-111">Diğer bir deyişle, [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ve [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)arasında gerçekleşenler hariç herhangi bir geri aramadan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0693c-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0693c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0693c-112">Requirements</span></span>  
 <span data-ttu-id="0693c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0693c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0693c-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0693c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0693c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0693c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0693c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0693c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0693c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0693c-117">See also</span></span>

- [<span data-ttu-id="0693c-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0693c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0693c-119">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0693c-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
