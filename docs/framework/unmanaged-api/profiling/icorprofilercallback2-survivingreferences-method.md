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
ms.openlocfilehash: fc3ec00f11582ede1dc4b3d481a4eb9dcc4dd1d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963909"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="640d2-102">ICorProfilerCallback2::SurvivingReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="640d2-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="640d2-103">Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.</span><span class="sxs-lookup"><span data-stu-id="640d2-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="640d2-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="640d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="640d2-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="640d2-106">'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="640d2-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="640d2-107">Diğer bir deyişle, değeri `cSurvivingObjectIDRanges` , her nesne bloğu için sırasıyla bir `cObjectIDRangeLength` `ObjectID` ve uzunluğu depolayan `objectIDRangeStart` ve dizilerinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="640d2-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="640d2-108">Sonraki iki bağımsız değişkeni `SurvivingReferences` paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="640d2-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="640d2-109">Diğer bir deyişle, `objectIDRangeStart` `cObjectIDRangeLength` aynı bitişik nesne bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="640d2-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="640d2-110">'ndaki Her biri, `ObjectID` bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="640d2-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="640d2-111">'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="640d2-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="640d2-112">`objectIDRangeStart` Dizide başvurulan her bir blok için bir boyut belirtilir.</span><span class="sxs-lookup"><span data-stu-id="640d2-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="640d2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="640d2-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="640d2-114">Bu yöntem, 64- `MAX_ULONG` bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar.</span><span class="sxs-lookup"><span data-stu-id="640d2-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="640d2-115">4 GB 'den büyük nesneler için bunun yerine [ICorProfilerCallback4:: SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="640d2-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="640d2-116">`objectIDRangeStart` Ve`cObjectIDRangeLength` dizilerinin öğeleri, bir nesnenin çöp toplamayı daha fazla kullanıp kullanmadığını anlamak için aşağıdaki şekilde yorumlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="640d2-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="640d2-117">Bir `ObjectID` değerin (`ObjectID`) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="640d2-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="640d2-118">Aşağıdaki aralıkta `i` olan herhangi bir değeri için, nesne çöp toplamayı sona bıraktı:</span><span class="sxs-lookup"><span data-stu-id="640d2-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="640d2-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="640d2-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="640d2-120">Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz.</span><span class="sxs-lookup"><span data-stu-id="640d2-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="640d2-121">Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="640d2-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="640d2-122">Ortak dil çalışma zamanı (CLR), `SurvivingReferences` sıkıştırma olmayan çöp koleksiyonları için çağırır.</span><span class="sxs-lookup"><span data-stu-id="640d2-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="640d2-123">Atık koleksiyonları sıkıştırmak için, bunun yerine [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="640d2-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="640d2-124">Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="640d2-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="640d2-125">Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences` geri çağırma `MovedReferences` ya da geri çağırma alır, ancak her ikisini birden etmez.</span><span class="sxs-lookup"><span data-stu-id="640d2-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="640d2-126">Sınırlı `SurvivingReferences` iç arabelleğe alma, sunucu çöp toplama durumunda birden çok iş parçacığı raporlama ve diğer nedenlerden dolayı belirli bir atık toplama sırasında birden fazla geri çağırma alınabilir.</span><span class="sxs-lookup"><span data-stu-id="640d2-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="640d2-127">Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir. herhangi bir `SurvivingReferences` geri aramada bildirilen tüm başvurular çöp toplamayı sürdürmelidir.</span><span class="sxs-lookup"><span data-stu-id="640d2-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="640d2-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="640d2-128">Requirements</span></span>  
 <span data-ttu-id="640d2-129">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="640d2-130">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="640d2-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="640d2-131">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="640d2-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="640d2-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640d2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640d2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640d2-133">See also</span></span>

- [<span data-ttu-id="640d2-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640d2-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="640d2-135">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640d2-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="640d2-136">SurvivingReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="640d2-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
