---
description: 'Daha fazla bilgi edinin: COR_PRF_GC_GENERATION_RANGE yapısı'
title: COR_PRF_GC_GENERATION_RANGE Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: ea67a6e6b972b9406b84ad331e8af6189327c5ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648928"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="e6f44-103">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="e6f44-103">COR_PRF_GC_GENERATION_RANGE Structure</span></span>

<span data-ttu-id="e6f44-104">Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6f44-104">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f44-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6f44-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="e6f44-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e6f44-106">Members</span></span>  
  
|<span data-ttu-id="e6f44-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e6f44-107">Member</span></span>|<span data-ttu-id="e6f44-108">Description</span><span class="sxs-lookup"><span data-stu-id="e6f44-108">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="e6f44-109">Bellek bloğunun ait olduğu üretimi belirten [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="e6f44-109">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="e6f44-110">Bellek bloğunun başlangıç konumunu belirten nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e6f44-110">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="e6f44-111">Bellek bloğunun kullanılan kısmının boyutunu belirten tamsayı işaretçisi (yani, blok içinde kullanılan bellek miktarı).</span><span class="sxs-lookup"><span data-stu-id="e6f44-111">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="e6f44-112">Bellek bloğunun boyutunu belirten bir tamsayı işaretçisi (yani, blok için ayrılan bellek miktarı).</span><span class="sxs-lookup"><span data-stu-id="e6f44-112">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f44-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6f44-113">Remarks</span></span>  

 <span data-ttu-id="e6f44-114">`rangeLength`Değerin yalnızca ICorProfilerInfo2:: GarbageCollectionStarted veya ICorProfilerCallback2:: GarbageCollectionFinished yönteminden çağrılan, [:: Getgenerationlimiti](icorprofilerinfo2-getgenerationbounds-method.md) veya [ICorProfilerInfo2:: GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), her ikisi de olan `COR_PRF_GC_GENERATION_RANGE` . [](icorprofilercallback2-garbagecollectionstarted-method.md) [](icorprofilercallback2-garbagecollectionfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="e6f44-114">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f44-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6f44-115">Requirements</span></span>  

 <span data-ttu-id="e6f44-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f44-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f44-117">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="e6f44-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e6f44-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6f44-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6f44-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f44-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f44-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f44-120">See also</span></span>

- [<span data-ttu-id="e6f44-121">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="e6f44-121">Profiling Structures</span></span>](profiling-structures.md)
