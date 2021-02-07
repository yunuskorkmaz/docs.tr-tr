---
description: ': ICorProfilerCallback:: ObjectReferences yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ObjectReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 55ea6fae87ecb6534af322fc9d5055c8a247f37a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745118"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="b1f7f-103">ICorProfilerCallback::ObjectReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1f7f-103">ICorProfilerCallback::ObjectReferences Method</span></span>

<span data-ttu-id="b1f7f-104">Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-104">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f7f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1f7f-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1f7f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1f7f-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="b1f7f-107">'ndaki Nesnelere başvuran nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-107">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="b1f7f-108">'ndaki Belirtilen nesnenin bir örneği olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-108">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="b1f7f-109">'ndaki Belirtilen nesnenin başvurduğu nesne sayısı (yani, dizideki öğelerin sayısı `objectRefIds` ).</span><span class="sxs-lookup"><span data-stu-id="b1f7f-109">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="b1f7f-110">'ndaki Tarafından başvurulan nesnelerin bir dizi kimliği `objectId` .</span><span class="sxs-lookup"><span data-stu-id="b1f7f-110">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1f7f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1f7f-111">Remarks</span></span>  

 <span data-ttu-id="b1f7f-112">`ObjectReferences`Bir çöp toplama işlemi tamamlandıktan sonra yığında kalan her nesne için yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-112">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="b1f7f-113">Profil Oluşturucu bu geri aramadan bir hata döndürürse, profil oluşturma hizmetleri sonraki atık toplamaya kadar bu geri aramayı çağırmayı sona erecek.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-113">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="b1f7f-114">`ObjectReferences`Geri çağırma [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) geri çağırması ile birlikte kullanılabilir ve çalışma zamanı için tamamen bir nesne başvurusu grafiği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-114">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="b1f7f-115">Ortak dil çalışma zamanı (CLR), her bir nesne başvurusunun yöntemi tarafından yalnızca bir kez bildirilmesini sağlar `ObjectReferences` .</span><span class="sxs-lookup"><span data-stu-id="b1f7f-115">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="b1f7f-116">`ObjectReferences`Çöp toplama nesnelerin ortasında olabileceğinden, tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-116">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="b1f7f-117">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `ObjectReferences` .</span><span class="sxs-lookup"><span data-stu-id="b1f7f-117">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="b1f7f-118">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında, çöp toplama tamamlanmıştır ve denetleme güvenle yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-118">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="b1f7f-119">Null değeri, `ClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-119">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f7f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1f7f-120">Requirements</span></span>  

 <span data-ttu-id="b1f7f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1f7f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f7f-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1f7f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1f7f-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1f7f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1f7f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f7f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f7f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f7f-125">See also</span></span>

- [<span data-ttu-id="b1f7f-126">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1f7f-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
