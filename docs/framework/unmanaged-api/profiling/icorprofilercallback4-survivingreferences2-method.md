---
title: ICorProfilerCallback4::SurvivingReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad96224daf79b17d3902217af061173580f1478a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122284"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="3d087-102">ICorProfilerCallback4::SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d087-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="3d087-103">Sıkıştırma dışı bir atık toplama sonucunda yığın nesnelerin yerleşimini bildirir.</span><span class="sxs-lookup"><span data-stu-id="3d087-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="3d087-104">Profil Oluşturucu uygulanırsa, bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3d087-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="3d087-105">Bu geri çağırma değiştirir [Icorprofilercallback2::survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesne aralıklarını rapor edebilirsiniz çünkü.</span><span class="sxs-lookup"><span data-stu-id="3d087-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d087-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d087-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d087-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d087-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="3d087-108">[in] Sıkıştırma olmayan çöp toplama işleminin sonucu olarak kurtulan bitişik nesnelerin blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="3d087-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="3d087-109">Diğer bir deyişle, değerini `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluğu, nesnelerin her blok için sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="3d087-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="3d087-110">Sonraki iki bağımsız değişkenleri `SurvivingReferences2` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="3d087-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="3d087-111">Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesnelerin aynı blok ilgilendiriyor.</span><span class="sxs-lookup"><span data-stu-id="3d087-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="3d087-112">[in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="3d087-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="3d087-113">[in] Her biri bellekte bitişik nesnelerin sürdüren bir blok boyutu olan bir tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="3d087-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="3d087-114">Başvurulduğundan her blok için belirtilen bir boyutu `objectIDRangeStart` dizisi.</span><span class="sxs-lookup"><span data-stu-id="3d087-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d087-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d087-115">Remarks</span></span>  
 <span data-ttu-id="3d087-116">Öğeleri `objectIDRangeStart` ve `cObjectIDRangeLength` diziler yorumlanabilir gibi bir nesne çöp toplamadan kurtulan olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="3d087-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="3d087-117">Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralığında yer:</span><span class="sxs-lookup"><span data-stu-id="3d087-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="3d087-118">İçin herhangi bir değerini `i` aşağıdaki aralığında olan, nesnenin çöp toplamadan kurtulan:</span><span class="sxs-lookup"><span data-stu-id="3d087-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="3d087-119">0 <= `i` < </span><span class="sxs-lookup"><span data-stu-id="3d087-119">0 <= `i` < </span></span>`cSurvivingObjectIDRanges`  
  
 <span data-ttu-id="3d087-120">Sıkıştırma dışı bir atık toplama "etkin olmayan" nesnelerin kapladığı belleği geri kazanır, ancak serbest bırakılan bu alanı compact değil.</span><span class="sxs-lookup"><span data-stu-id="3d087-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="3d087-121">Sonuç olarak, bellek için yığın döndürülür, ancak "canlı" nesne taşındı.</span><span class="sxs-lookup"><span data-stu-id="3d087-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="3d087-122">Ortak dil çalışma zamanı (CLR) çağıran `SurvivingReferences2` sıkıştırma olmayan çöp toplama için.</span><span class="sxs-lookup"><span data-stu-id="3d087-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="3d087-123">Sıkıştırma çöp koleksiyonları için [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d087-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="3d087-124">Tek bir çöp toplama, tek bir nesil için sıkıştırma ve diğer olmayan sıkıştırma olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d087-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="3d087-125">Herhangi belirli nesil çöp toplama için profil oluşturucu ya da alacak bir `SurvivingReferences2` geri çağırma veya bir [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) geri çağırma, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="3d087-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="3d087-126">Birden çok `SurvivingReferences2` geri çağırmaları alınan sınırlı iç arabelleğe alma nedeniyle ek olarak, belirli bir çöp toplama, sunucu çöp toplama sırasında birden çok geri çağırmaları ve diğer nedenlerle sırasında.</span><span class="sxs-lookup"><span data-stu-id="3d087-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="3d087-127">Bir çöp toplama sırasında birden çok geri çağırmaları söz konusu olduğunda, bilgileri toplu olarak; içinde bildirilen tüm başvuruları `SurvivingReferences2` çöp toplama geri çağırma önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3d087-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="3d087-128">Profil Oluşturucu hem de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri `SurvivingReferences2` önce yöntemi çağrıldığında [Icorprofilercallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, ancak yalnızca `SurvivingReferences2` başarıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d087-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="3d087-129">Profil oluşturucular hatasından gösteren HRESULT döndürebilir `SurvivingReferences2` yöntemi ikinci yöntem çağırmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="3d087-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d087-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d087-130">Requirements</span></span>  
 <span data-ttu-id="3d087-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d087-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d087-132">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d087-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d087-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d087-133">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3d087-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3d087-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d087-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d087-135">See also</span></span>

- [<span data-ttu-id="3d087-136">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d087-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3d087-137">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d087-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="3d087-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d087-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
