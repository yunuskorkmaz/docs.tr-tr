---
title: "ICorProfilerCallback::ObjectReferences Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdebc1984f86d3801759f8f987df8fb89d82e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="576c2-102">ICorProfilerCallback::ObjectReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="576c2-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="576c2-103">Profil Oluşturucu belirtilen nesne tarafından başvurulan bellek nesneleri hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="576c2-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="576c2-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="576c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="576c2-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="576c2-106">[in] Nesnelere başvurma nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="576c2-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="576c2-107">[in] Belirtilen nesne örneği sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="576c2-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="576c2-108">[in] Belirtilen nesne tarafından başvurulan nesne sayısı (diğer bir deyişle, öğe sayısı `objectRefIds` array).</span><span class="sxs-lookup"><span data-stu-id="576c2-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="576c2-109">[in] Tarafından başvurulan kimlikleri nesnelerinin bir dizisi `objectId`.</span><span class="sxs-lookup"><span data-stu-id="576c2-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="576c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="576c2-110">Remarks</span></span>  
 <span data-ttu-id="576c2-111">`ObjectReferences` Yöntemi yığınında çöp toplama tamamlandıktan sonra geri kalan her bir nesne için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="576c2-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="576c2-112">Profil Oluşturucu bu geri aramasından hata verirse, profil oluşturma hizmetleri sonraki çöp toplama kadar bu geri çağırma devam etmeyecek.</span><span class="sxs-lookup"><span data-stu-id="576c2-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="576c2-113">`ObjectReferences` Geri çağırma ile birlikte kullanılabilir [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) çalışma zamanı için tam nesne başvurusu grafik oluşturmak için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="576c2-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="576c2-114">Ortak dil çalışma zamanı (CLR) her nesne başvurusu tarafından yalnızca bir kez bildirilir sağlar `ObjectReferences` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="576c2-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="576c2-115">Tarafından döndürülen nesne kimlikleri `ObjectReferences` çöp toplama nesneleri taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="576c2-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="576c2-116">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ObjectReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="576c2-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="576c2-117">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) çağrılır, atık toplama tamamlandığında ve İnceleme güvenle yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="576c2-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="576c2-118">Bir null `ClassId` belirten `objectId` kaldırdığı bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="576c2-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="576c2-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="576c2-119">Requirements</span></span>  
 <span data-ttu-id="576c2-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="576c2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="576c2-121">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="576c2-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="576c2-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="576c2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="576c2-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="576c2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576c2-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="576c2-124">See Also</span></span>  
 [<span data-ttu-id="576c2-125">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="576c2-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
