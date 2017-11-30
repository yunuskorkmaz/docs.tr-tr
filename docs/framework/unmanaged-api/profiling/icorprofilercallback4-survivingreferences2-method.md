---
title: "ICorProfilerCallback4::SurvivingReferences2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ced8542d2e84b6c317e20d7ff440e6c159383bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="3283a-102">ICorProfilerCallback4::SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3283a-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="3283a-103">Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir.</span><span class="sxs-lookup"><span data-stu-id="3283a-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="3283a-104">Profil Oluşturucu uygulanırsa bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3283a-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="3283a-105">Bu geri çağırma değiştirir [Icorprofilercallback2::survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesneleri aralıklarına raporlayabilirsiniz olduğundan.</span><span class="sxs-lookup"><span data-stu-id="3283a-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3283a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3283a-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3283a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3283a-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="3283a-108">[in] Sıkıştırılmasını olmayan çöp toplama sonucu olarak derdi bitti bitişik nesnelerin bloğu sayısı.</span><span class="sxs-lookup"><span data-stu-id="3283a-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="3283a-109">Diğer bir deyişle, değeri `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluk, sırasıyla, her bir bloğunda nesneleri için.</span><span class="sxs-lookup"><span data-stu-id="3283a-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="3283a-110">Sonraki iki bağımsız değişkenleri `SurvivingReferences2` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="3283a-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="3283a-111">Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesneleri aynı bloğunu ilgilendiren.</span><span class="sxs-lookup"><span data-stu-id="3283a-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="3283a-112">[in] Bir dizi `ObjectID` her biri bitişik bloğunun başlangıç adresi olduğunda, değerleri, bellekte nesneleri canlı.</span><span class="sxs-lookup"><span data-stu-id="3283a-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="3283a-113">[in] Her biri sağlam bir blok bellekte bitişik nesnelerin boyutudur dizisi.</span><span class="sxs-lookup"><span data-stu-id="3283a-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="3283a-114">Başvuru her blok için belirtilen bir boyutu `objectIDRangeStart` dizi.</span><span class="sxs-lookup"><span data-stu-id="3283a-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3283a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3283a-115">Remarks</span></span>  
 <span data-ttu-id="3283a-116">Öğelerini `objectIDRangeStart` ve `cObjectIDRangeLength` diziler kabul aşağıdaki gibi bir nesne atık toplama derdi bitti olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="3283a-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="3283a-117">Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralık içinde yer:</span><span class="sxs-lookup"><span data-stu-id="3283a-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="3283a-118">Herhangi bir değer için `i` aşağıdaki aralıkta olduğundan, nesne çöp toplama derdi bitti:</span><span class="sxs-lookup"><span data-stu-id="3283a-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="3283a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="3283a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="3283a-120">Sıkıştırılmasını olmayan çöp toplama "ölü" nesneleri tarafından kapladığı bellek kaldırsa ancak boşaltılmış alan compact değil.</span><span class="sxs-lookup"><span data-stu-id="3283a-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="3283a-121">Sonuç olarak, bellek için yığın döndürüldü, ancak hiçbir "canlı" nesneler taşınır.</span><span class="sxs-lookup"><span data-stu-id="3283a-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="3283a-122">Ortak dil çalışma zamanı (CLR) çağırır `SurvivingReferences2` sıkıştırılmasını olmayan çöp koleksiyonları için.</span><span class="sxs-lookup"><span data-stu-id="3283a-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="3283a-123">Sıkıştırma çöp koleksiyonları için [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yerine olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3283a-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="3283a-124">Tek çöp toplama, tek bir nesil sıkıştırma ve diğer olmayan sıkıştırılmasını olabilir.</span><span class="sxs-lookup"><span data-stu-id="3283a-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="3283a-125">Belirli bir oluşturma hakkında bir atık toplama için profil oluşturucu ya da alacak bir `SurvivingReferences2` geri çağırma veya bir [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) geri çağırma, ancak ikisini.</span><span class="sxs-lookup"><span data-stu-id="3283a-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="3283a-126">Birden çok `SurvivingReferences2` geri aramalar alınan sınırlı iç arabelleğe alma nedeniyle ek olarak, belirli atık toplama, sunucu çöp toplama sırasında birden çok geri aramalar ve diğer nedenler sırasında.</span><span class="sxs-lookup"><span data-stu-id="3283a-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="3283a-127">Çöp toplama sırasında birden çok geri aramalar söz konusu olduğunda toplu bilgileridir; içinde bildirilen tüm başvuruları `SurvivingReferences2` geri çağırma varlığını sürdürmesini atık toplama.</span><span class="sxs-lookup"><span data-stu-id="3283a-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="3283a-128">Profil Oluşturucu her ikisi de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri, `SurvivingReferences2` yöntemi çağrılmadan önce [Icorprofilercallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, ancak yalnızca `SurvivingReferences2` başarıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="3283a-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="3283a-129">Profil oluşturucular hatasından gösteren bir HRESULT dönebilirsiniz `SurvivingReferences2` ikinci yöntem çağırma önlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3283a-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3283a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3283a-130">Requirements</span></span>  
 <span data-ttu-id="3283a-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3283a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3283a-132">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3283a-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3283a-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3283a-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3283a-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3283a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3283a-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3283a-135">See Also</span></span>  
 [<span data-ttu-id="3283a-136">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="3283a-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3283a-137">Icorprofilercallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3283a-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="3283a-138">Icorprofilercallback4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3283a-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
