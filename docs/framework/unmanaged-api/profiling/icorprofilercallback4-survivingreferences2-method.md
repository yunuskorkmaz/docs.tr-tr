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
ms.openlocfilehash: 208ce1d7ef8a1eab4f18a6d488f0cc480b5713d8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499343"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="e6efe-102">ICorProfilerCallback4::SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6efe-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="e6efe-103">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="e6efe-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="e6efe-104">Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e6efe-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="e6efe-105">Bu geri çağırma, [ICorProfilerCallback2:: Evingreferences](icorprofilercallback2-survivingreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda bir ULONG 'ta belirtilebilecekleri daha büyük aralıklar bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="e6efe-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6efe-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e6efe-106">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6efe-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6efe-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="e6efe-108">'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="e6efe-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="e6efe-109">Diğer bir deyişle, değeri, `cSurvivingObjectIDRanges` `objectIDRangeStart` `cObjectIDRangeLength` `ObjectID` her nesne bloğu için sırasıyla bir ve uzunluğu depolayan ve dizilerinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="e6efe-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="e6efe-110">Sonraki iki bağımsız değişkeni `SurvivingReferences2` paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="e6efe-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="e6efe-111">Diğer bir deyişle, `objectIDRangeStart` `cObjectIDRangeLength` aynı bitişik nesne bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="e6efe-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="e6efe-112">'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="e6efe-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="e6efe-113">'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="e6efe-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="e6efe-114">Dizide başvurulan her bir blok için bir boyut belirtilir `objectIDRangeStart` .</span><span class="sxs-lookup"><span data-stu-id="e6efe-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6efe-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6efe-115">Remarks</span></span>  
 <span data-ttu-id="e6efe-116">Ve dizilerinin öğeleri, `objectIDRangeStart` `cObjectIDRangeLength` bir nesnenin çöp toplamayı daha fazla kullanıp kullanmadığını anlamak için aşağıdaki şekilde yorumlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6efe-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="e6efe-117">Bir `ObjectID` değerin ( `ObjectID` ) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="e6efe-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="e6efe-118">Aşağıdaki aralıkta olan herhangi bir değeri için `i` , nesne çöp toplamayı sona bıraktı:</span><span class="sxs-lookup"><span data-stu-id="e6efe-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="e6efe-119">0 <=`i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="e6efe-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="e6efe-120">Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz.</span><span class="sxs-lookup"><span data-stu-id="e6efe-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="e6efe-121">Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="e6efe-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="e6efe-122">Ortak dil çalışma zamanı (CLR), `SurvivingReferences2` sıkıştırma olmayan çöp koleksiyonları için çağırır.</span><span class="sxs-lookup"><span data-stu-id="e6efe-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="e6efe-123">Atık koleksiyonları sıkıştırmak için, bunun yerine [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e6efe-123">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="e6efe-124">Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6efe-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="e6efe-125">Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences2` geri çağırma veya [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri çağırması alır, ancak her ikisini birden etmez.</span><span class="sxs-lookup"><span data-stu-id="e6efe-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="e6efe-126">`SurvivingReferences2`Belirli bir çöp toplama işlemi sırasında, sınırlı iç arabellek, sunucu çöp toplama sırasında birden fazla geri çağırma ve diğer nedenlerden dolayı birden fazla geri çağırma alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e6efe-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="e6efe-127">Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir; herhangi bir `SurvivingReferences2` geri çağırmada raporlanan tüm başvurular çöp toplamayı sürdürmemiştir.</span><span class="sxs-lookup"><span data-stu-id="e6efe-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="e6efe-128">Profil Oluşturucu hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `SurvivingReferences2` yöntemi [ICorProfilerCallback2:: ıvınreferences](icorprofilercallback2-survivingreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `SurvivingReferences2` başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e6efe-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="e6efe-129">Profil oluşturucular `SurvivingReferences2` , ikinci yöntemi çağırmayı önlemek için yöntemden hata belirten BIR hresult döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="e6efe-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6efe-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6efe-130">Requirements</span></span>  
 <span data-ttu-id="e6efe-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6efe-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6efe-132">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e6efe-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6efe-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6efe-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6efe-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6efe-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6efe-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6efe-135">See also</span></span>

- [<span data-ttu-id="e6efe-136">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6efe-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e6efe-137">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6efe-137">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="e6efe-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6efe-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
