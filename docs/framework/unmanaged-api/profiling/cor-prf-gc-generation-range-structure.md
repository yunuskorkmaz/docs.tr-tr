---
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
ms.openlocfilehash: 0bdb8cd02e0beb69e3ec594b0aadd741a5f0d924
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428341"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="0efc6-102">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="0efc6-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="0efc6-103">Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.</span><span class="sxs-lookup"><span data-stu-id="0efc6-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0efc6-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="0efc6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0efc6-105">Members</span></span>  
  
|<span data-ttu-id="0efc6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0efc6-106">Member</span></span>|<span data-ttu-id="0efc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0efc6-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="0efc6-108">Bellek bloğunun ait olduğu üretimi belirten [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="0efc6-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="0efc6-109">Bellek bloğunun başlangıç konumunu belirten nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0efc6-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="0efc6-110">Bellek bloğunun kullanılan kısmının boyutunu belirten tamsayı işaretçisi (yani, blok içinde kullanılan bellek miktarı).</span><span class="sxs-lookup"><span data-stu-id="0efc6-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="0efc6-111">Bellek bloğunun boyutunu belirten bir tamsayı işaretçisi (yani, blok için ayrılan bellek miktarı).</span><span class="sxs-lookup"><span data-stu-id="0efc6-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0efc6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0efc6-112">Remarks</span></span>  
 <span data-ttu-id="0efc6-113">`rangeLength` değeri yalnızca [ICorProfilerInfo2:: Getgenerationlimiti](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) veya [ICorProfilerInfo2:: GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), her ikisi `COR_PRF_GC_GENERATION_RANGE` de [ICorProfilerCallback2:: GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) veya [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) yönteminden çağrıldığında doğru olarak garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="0efc6-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efc6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0efc6-114">Requirements</span></span>  
 <span data-ttu-id="0efc6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0efc6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0efc6-116">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="0efc6-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0efc6-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0efc6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0efc6-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0efc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0efc6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0efc6-119">See also</span></span>

- [<span data-ttu-id="0efc6-120">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="0efc6-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
