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
ms.openlocfilehash: 798815c1122129395e57ff1274c23292696504f0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865720"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="479f0-102">ICorProfilerCallback2::SurvivingReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="479f0-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="479f0-103">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="479f0-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="479f0-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="479f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="479f0-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="479f0-106">'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="479f0-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="479f0-107">Diğer bir deyişle, `cSurvivingObjectIDRanges` değeri, her nesne bloğu için sırasıyla bir `ObjectID` ve uzunluğu depolayan `objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="479f0-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="479f0-108">`SurvivingReferences` sonraki iki bağımsız değişkeni paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="479f0-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="479f0-109">Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` aynı bitişik nesne bloğunu ilgilendirin.</span><span class="sxs-lookup"><span data-stu-id="479f0-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="479f0-110">'ndaki Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan `ObjectID` değerlerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="479f0-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="479f0-111">'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="479f0-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="479f0-112">`objectIDRangeStart` dizisinde başvurulan her bir blok için bir boyut belirtilir.</span><span class="sxs-lookup"><span data-stu-id="479f0-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="479f0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="479f0-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="479f0-114">Bu yöntem, 64-bit platformlarda 4 GB 'tan büyük nesneler için boyutları `MAX_ULONG` olarak raporlar.</span><span class="sxs-lookup"><span data-stu-id="479f0-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="479f0-115">4 GB 'den büyük nesneler için bunun yerine [ICorProfilerCallback4:: SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="479f0-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="479f0-116">`objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin öğeleri, bir nesnenin çöp toplamayı bir daha fazla kullanıp kullanmadığını belirlemekte aşağıdaki şekilde yorumlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="479f0-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="479f0-117">`ObjectID` bir değerin (`ObjectID`) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="479f0-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="479f0-118">Aşağıdaki aralıktaki `i` herhangi bir değeri için, nesne çöp toplamayı sona bıraktı:</span><span class="sxs-lookup"><span data-stu-id="479f0-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="479f0-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="479f0-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="479f0-120">Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz.</span><span class="sxs-lookup"><span data-stu-id="479f0-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="479f0-121">Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="479f0-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="479f0-122">Ortak dil çalışma zamanı (CLR), sıkıştırma olmayan çöp koleksiyonları için `SurvivingReferences` çağırır.</span><span class="sxs-lookup"><span data-stu-id="479f0-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="479f0-123">Atık koleksiyonları sıkıştırmak için, bunun yerine [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="479f0-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="479f0-124">Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="479f0-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="479f0-125">Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences` geri çağırma veya `MovedReferences` geri çağırması alır, ancak her ikisini birden etmez.</span><span class="sxs-lookup"><span data-stu-id="479f0-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="479f0-126">Belirli bir çöp toplama işlemi sırasında, sınırlı iç arabellek, sunucu çöp toplama durumunda birden çok iş parçacığı raporlama ve diğer nedenlerden dolayı birden çok `SurvivingReferences` geri çağırmaları alınabilir.</span><span class="sxs-lookup"><span data-stu-id="479f0-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="479f0-127">Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir. herhangi bir `SurvivingReferences` geri aramada bildirilen tüm başvurular çöp toplama işlemini sürdürmelidir.</span><span class="sxs-lookup"><span data-stu-id="479f0-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="479f0-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="479f0-128">Requirements</span></span>  
 <span data-ttu-id="479f0-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="479f0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479f0-130">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="479f0-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="479f0-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="479f0-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="479f0-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="479f0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479f0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="479f0-133">See also</span></span>

- [<span data-ttu-id="479f0-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="479f0-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="479f0-135">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="479f0-135">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="479f0-136">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="479f0-136">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
