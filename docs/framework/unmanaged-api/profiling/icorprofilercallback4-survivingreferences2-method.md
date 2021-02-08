---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback4:: SurvivingReferences2 yöntemi'
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
ms.openlocfilehash: d092729c77b0c4feb253bb2f54968f7ff8bdbb2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788689"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="46f9a-103">ICorProfilerCallback4::SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46f9a-103">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>

<span data-ttu-id="46f9a-104">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="46f9a-104">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="46f9a-105">Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="46f9a-105">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="46f9a-106">Bu geri çağırma, [ICorProfilerCallback2:: Evingreferences](icorprofilercallback2-survivingreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda bir ULONG 'ta belirtilebilecekleri daha büyük aralıklar bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="46f9a-106">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f9a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46f9a-107">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="46f9a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46f9a-108">Parameters</span></span>  

 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="46f9a-109">'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="46f9a-109">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="46f9a-110">Diğer bir deyişle, değeri, `cSurvivingObjectIDRanges` `objectIDRangeStart` `cObjectIDRangeLength` `ObjectID` her nesne bloğu için sırasıyla bir ve uzunluğu depolayan ve dizilerinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="46f9a-110">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="46f9a-111">Sonraki iki bağımsız değişkeni `SurvivingReferences2` paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="46f9a-111">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="46f9a-112">Diğer bir deyişle, `objectIDRangeStart` `cObjectIDRangeLength` aynı bitişik nesne bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="46f9a-112">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="46f9a-113">'ndaki `ObjectID` Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="46f9a-113">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="46f9a-114">'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="46f9a-114">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="46f9a-115">Dizide başvurulan her bir blok için bir boyut belirtilir `objectIDRangeStart` .</span><span class="sxs-lookup"><span data-stu-id="46f9a-115">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46f9a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46f9a-116">Remarks</span></span>  

 <span data-ttu-id="46f9a-117">Ve dizilerinin öğeleri, `objectIDRangeStart` `cObjectIDRangeLength` bir nesnenin çöp toplamayı daha fazla kullanıp kullanmadığını anlamak için aşağıdaki şekilde yorumlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46f9a-117">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="46f9a-118">Bir `ObjectID` değerin ( `ObjectID` ) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="46f9a-118">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="46f9a-119">Aşağıdaki aralıkta olan herhangi bir değeri için `i` , nesne çöp toplamayı sona bıraktı:</span><span class="sxs-lookup"><span data-stu-id="46f9a-119">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="46f9a-120">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="46f9a-120">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="46f9a-121">Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz.</span><span class="sxs-lookup"><span data-stu-id="46f9a-121">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="46f9a-122">Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="46f9a-122">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="46f9a-123">Ortak dil çalışma zamanı (CLR), `SurvivingReferences2` sıkıştırma olmayan çöp koleksiyonları için çağırır.</span><span class="sxs-lookup"><span data-stu-id="46f9a-123">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="46f9a-124">Atık koleksiyonları sıkıştırmak için, bunun yerine [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) çağırılır.</span><span class="sxs-lookup"><span data-stu-id="46f9a-124">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="46f9a-125">Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="46f9a-125">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="46f9a-126">Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences2` geri çağırma veya [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri çağırması alır, ancak her ikisini birden etmez.</span><span class="sxs-lookup"><span data-stu-id="46f9a-126">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="46f9a-127">`SurvivingReferences2`Belirli bir çöp toplama işlemi sırasında, sınırlı iç arabellek, sunucu çöp toplama sırasında birden fazla geri çağırma ve diğer nedenlerden dolayı birden fazla geri çağırma alınabilir.</span><span class="sxs-lookup"><span data-stu-id="46f9a-127">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="46f9a-128">Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir; herhangi bir `SurvivingReferences2` geri çağırmada raporlanan tüm başvurular çöp toplamayı sürdürmemiştir.</span><span class="sxs-lookup"><span data-stu-id="46f9a-128">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="46f9a-129">Profil Oluşturucu hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `SurvivingReferences2` yöntemi [ICorProfilerCallback2:: ıvınreferences](icorprofilercallback2-survivingreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `SurvivingReferences2` başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="46f9a-129">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="46f9a-130">Profil oluşturucular `SurvivingReferences2` , ikinci yöntemi çağırmayı önlemek için yöntemden hata belirten BIR hresult döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="46f9a-130">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f9a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46f9a-131">Requirements</span></span>  

 <span data-ttu-id="46f9a-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46f9a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f9a-133">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="46f9a-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46f9a-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46f9a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46f9a-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f9a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f9a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46f9a-136">See also</span></span>

- [<span data-ttu-id="46f9a-137">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46f9a-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="46f9a-138">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46f9a-138">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="46f9a-139">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46f9a-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
