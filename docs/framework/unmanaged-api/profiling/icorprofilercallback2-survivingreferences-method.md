---
title: ICorProfilerCallback2::SurvivingReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0ed1dc09e8dcee8a4c67e01279c6e13661e252d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459833"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="e2f0d-102">ICorProfilerCallback2::SurvivingReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2f0d-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="e2f0d-103">Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2f0d-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2f0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2f0d-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="e2f0d-106">[in] Sıkıştırılmasını olmayan çöp toplama sonucu olarak derdi bitti bitişik nesnelerin bloğu sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="e2f0d-107">Diğer bir deyişle, değeri `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluk, sırasıyla, her bir bloğunda nesneleri için.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="e2f0d-108">Sonraki iki bağımsız değişkenleri `SurvivingReferences` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="e2f0d-109">Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesneleri aynı bloğunu ilgilendiren.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="e2f0d-110">[in] Bir dizi `ObjectID` her biri bitişik bloğunun başlangıç adresi olduğunda, değerleri, bellekte nesneleri canlı.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="e2f0d-111">[in] Her biri sağlam bir blok bellekte bitişik nesnelerin boyutudur dizisi.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="e2f0d-112">Başvuru her blok için belirtilen bir boyutu `objectIDRangeStart` dizi.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2f0d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2f0d-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2f0d-114">Bu yöntem olarak boyutlarını raporlar `MAX_ULONG` 64 bit platformlarda 4 GB'den büyük nesneler için.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="e2f0d-115">4 GB'den büyük nesneleri için kullanılmak [Icorprofilercallback4::survivingreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="e2f0d-116">Öğelerini `objectIDRangeStart` ve `cObjectIDRangeLength` diziler kabul aşağıdaki gibi bir nesne atık toplama derdi bitti olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="e2f0d-117">Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralık içinde yer:</span><span class="sxs-lookup"><span data-stu-id="e2f0d-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="e2f0d-118">Herhangi bir değer için `i` aşağıdaki aralıkta olduğundan, nesne çöp toplama derdi bitti:</span><span class="sxs-lookup"><span data-stu-id="e2f0d-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="e2f0d-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="e2f0d-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="e2f0d-120">Sıkıştırılmasını olmayan çöp toplama "ölü" nesneleri tarafından kapladığı bellek kaldırsa ancak boşaltılmış alan compact değil.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="e2f0d-121">Sonuç olarak, bellek için yığın döndürüldü, ancak hiçbir "canlı" nesneler taşınır.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="e2f0d-122">Ortak dil çalışma zamanı (CLR) çağırır `SurvivingReferences` sıkıştırılmasını olmayan çöp koleksiyonları için.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="e2f0d-123">Sıkıştırma çöp koleksiyonları için [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yerine olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="e2f0d-124">Tek çöp toplama, tek bir nesil sıkıştırma ve diğer olmayan sıkıştırılmasını olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="e2f0d-125">Belirli bir oluşturma hakkında bir atık toplama için profil oluşturucu ya da alacak bir `SurvivingReferences` geri çağırma veya bir `MovedReferences` geri çağırma, ancak ikisini.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="e2f0d-126">Birden çok `SurvivingReferences` geri aramalar alınan sınırlı iç arabelleğe alma, nedeniyle ek olarak, belirli atık toplama sırasında birden çok iş parçacığı sunucu çöp toplama ve diğer nedenler söz konusu olduğunda raporlama.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="e2f0d-127">Çöp toplama sırasında birden çok geri aramalar söz konusu olduğunda, bilgileri toplu — birinde raporlanan tüm başvuruları `SurvivingReferences` geri çağırma varlığını sürdürmesini atık toplama.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f0d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2f0d-128">Requirements</span></span>  
 <span data-ttu-id="e2f0d-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f0d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f0d-130">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2f0d-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2f0d-131">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2f0d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2f0d-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f0d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f0d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f0d-133">See Also</span></span>  
 [<span data-ttu-id="e2f0d-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2f0d-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e2f0d-135">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2f0d-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="e2f0d-136">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2f0d-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
