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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbeebc766d6e8048843a74691addd1dee90623ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621714"
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="05972-102">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="05972-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="05972-103">Çöp toplama aşamasında bir bellek aralığı (yani, blok) açıklar.</span><span class="sxs-lookup"><span data-stu-id="05972-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05972-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05972-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="05972-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="05972-105">Members</span></span>  
  
|<span data-ttu-id="05972-106">Üye</span><span class="sxs-lookup"><span data-stu-id="05972-106">Member</span></span>|<span data-ttu-id="05972-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05972-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="05972-108">Değerini [cor_prf_gc_generatıon](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) ait nesli olan bellek bloğunu belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="05972-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="05972-109">Bellek bloğunu başlangıç konumunu belirten bir nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="05972-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="05972-110">Kullanılan bellek bloğu (diğer bir deyişle, blok içinde kullanılan bellek miktarı) bölümü boyutunu belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="05972-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="05972-111">(Diğer bir deyişle, blok için ayrılmış bellek miktarı) bellek bloğu boyutunu belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="05972-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05972-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05972-112">Remarks</span></span>  
 <span data-ttu-id="05972-113">`rangeLength` Değeri doğru olarak garantisi yalnızca [Icorprofilerınfo2::getgenerationbounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) veya [Icorprofilerınfo2::getobjectgeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), hangi kullanım hem de `COR_PRF_GC_GENERATION_RANGE` Yapı, çağrılır [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) veya [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05972-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05972-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05972-114">Requirements</span></span>  
 <span data-ttu-id="05972-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05972-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05972-116">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="05972-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="05972-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05972-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05972-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05972-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05972-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05972-119">See also</span></span>
- [<span data-ttu-id="05972-120">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="05972-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
