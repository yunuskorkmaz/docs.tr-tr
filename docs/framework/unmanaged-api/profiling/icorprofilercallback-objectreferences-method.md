---
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
ms.openlocfilehash: 12a0792e8fafc73b480de6bacc86f98470dfedf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503295"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="c07a1-102">ICorProfilerCallback::ObjectReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c07a1-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="c07a1-103">Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c07a1-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07a1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c07a1-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c07a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c07a1-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c07a1-106">'ndaki Nesnelere başvuran nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c07a1-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="c07a1-107">'ndaki Belirtilen nesnenin bir örneği olduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c07a1-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="c07a1-108">'ndaki Belirtilen nesnenin başvurduğu nesne sayısı (yani, dizideki öğelerin sayısı `objectRefIds` ).</span><span class="sxs-lookup"><span data-stu-id="c07a1-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="c07a1-109">'ndaki Tarafından başvurulan nesnelerin bir dizi kimliği `objectId` .</span><span class="sxs-lookup"><span data-stu-id="c07a1-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c07a1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c07a1-110">Remarks</span></span>  
 <span data-ttu-id="c07a1-111">`ObjectReferences`Bir çöp toplama işlemi tamamlandıktan sonra yığında kalan her nesne için yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c07a1-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="c07a1-112">Profil Oluşturucu bu geri aramadan bir hata döndürürse, profil oluşturma hizmetleri sonraki atık toplamaya kadar bu geri aramayı çağırmayı sona erecek.</span><span class="sxs-lookup"><span data-stu-id="c07a1-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="c07a1-113">`ObjectReferences`Geri çağırma [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) geri çağırması ile birlikte kullanılabilir ve çalışma zamanı için tamamen bir nesne başvurusu grafiği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c07a1-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="c07a1-114">Ortak dil çalışma zamanı (CLR), her bir nesne başvurusunun yöntemi tarafından yalnızca bir kez bildirilmesini sağlar `ObjectReferences` .</span><span class="sxs-lookup"><span data-stu-id="c07a1-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="c07a1-115">`ObjectReferences`Çöp toplama nesnelerin ortasında olabileceğinden, tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c07a1-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="c07a1-116">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `ObjectReferences` .</span><span class="sxs-lookup"><span data-stu-id="c07a1-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="c07a1-117">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında, çöp toplama tamamlanmıştır ve denetleme güvenle yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c07a1-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="c07a1-118">Null değeri, `ClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c07a1-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c07a1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c07a1-119">Requirements</span></span>  
 <span data-ttu-id="c07a1-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c07a1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c07a1-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c07a1-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c07a1-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c07a1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c07a1-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c07a1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07a1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c07a1-124">See also</span></span>

- [<span data-ttu-id="c07a1-125">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c07a1-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
