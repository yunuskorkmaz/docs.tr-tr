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
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191308"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="2895d-102">ICorProfilerCallback2::SurvivingReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2895d-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="2895d-103">Sıkıştırma dışı bir atık toplama sonucunda yığın nesnelerin yerleşimini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2895d-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2895d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2895d-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2895d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2895d-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="2895d-106">[in] Sıkıştırma olmayan çöp toplama işleminin sonucu olarak kurtulan bitişik nesnelerin blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="2895d-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="2895d-107">Diğer bir deyişle, değerini `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluğu, nesnelerin her blok için sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="2895d-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="2895d-108">Sonraki iki bağımsız değişkenleri `SurvivingReferences` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="2895d-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="2895d-109">Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesnelerin aynı blok ilgilendiriyor.</span><span class="sxs-lookup"><span data-stu-id="2895d-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="2895d-110">[in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="2895d-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="2895d-111">[in] Her biri bellekte bitişik nesnelerin sürdüren bir blok boyutu olan bir tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="2895d-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="2895d-112">Başvurulduğundan her blok için belirtilen bir boyutu `objectIDRangeStart` dizisi.</span><span class="sxs-lookup"><span data-stu-id="2895d-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2895d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2895d-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2895d-114">Bu yöntem boyutları olarak raporlar `MAX_ULONG` 64-bit platformlarda 4 GB'den büyük olan nesneler için.</span><span class="sxs-lookup"><span data-stu-id="2895d-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="2895d-115">4 GB'den daha büyük nesneleri için kullanılmak [Icorprofilercallback4::survivingreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="2895d-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="2895d-116">Öğeleri `objectIDRangeStart` ve `cObjectIDRangeLength` diziler yorumlanabilir gibi bir nesne çöp toplamadan kurtulan olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="2895d-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="2895d-117">Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralığında yer:</span><span class="sxs-lookup"><span data-stu-id="2895d-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="2895d-118">İçin herhangi bir değerini `i` aşağıdaki aralığında olan, nesnenin çöp toplamadan kurtulan:</span><span class="sxs-lookup"><span data-stu-id="2895d-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="2895d-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="2895d-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="2895d-120">Sıkıştırma dışı bir atık toplama "etkin olmayan" nesnelerin kapladığı belleği geri kazanır, ancak serbest bırakılan bu alanı compact değil.</span><span class="sxs-lookup"><span data-stu-id="2895d-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="2895d-121">Sonuç olarak, bellek için yığın döndürülür, ancak "canlı" nesne taşındı.</span><span class="sxs-lookup"><span data-stu-id="2895d-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="2895d-122">Ortak dil çalışma zamanı (CLR) çağıran `SurvivingReferences` sıkıştırma olmayan çöp toplama için.</span><span class="sxs-lookup"><span data-stu-id="2895d-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="2895d-123">Sıkıştırma çöp koleksiyonları için [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2895d-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="2895d-124">Tek bir çöp toplama, tek bir nesil için sıkıştırma ve diğer olmayan sıkıştırma olabilir.</span><span class="sxs-lookup"><span data-stu-id="2895d-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="2895d-125">Herhangi belirli nesil çöp toplama için profil oluşturucu ya da alacak bir `SurvivingReferences` geri çağırma veya bir `MovedReferences` geri çağırma, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="2895d-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="2895d-126">Birden çok `SurvivingReferences` geri çağırmaları alınan sınırlı iç arabelleğe, nedeniyle ek olarak, belirli bir çöp toplama sırasında raporlama sunucu çöp toplama ve diğer nedenlerle olması durumunda birden çok iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="2895d-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="2895d-127">Bir çöp toplama sırasında birden çok geri çağırmaları söz konusu olduğunda, bilgileri toplu — içinde bildirilen tüm başvuruları `SurvivingReferences` çöp toplama geri çağırma önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="2895d-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2895d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2895d-128">Requirements</span></span>  
 <span data-ttu-id="2895d-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2895d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2895d-130">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2895d-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2895d-131">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2895d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2895d-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2895d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2895d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2895d-133">See also</span></span>

- [<span data-ttu-id="2895d-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2895d-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2895d-135">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2895d-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="2895d-136">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2895d-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
