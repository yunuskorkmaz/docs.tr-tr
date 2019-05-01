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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942287"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="7e4f0-102">ICorProfilerCallback::ObjectReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e4f0-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="7e4f0-103">Profil Oluşturucu belirtilen nesne tarafından başvurulan nesneleri bellekte hakkında bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e4f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e4f0-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e4f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e4f0-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7e4f0-106">[in] Nesnelere başvurma nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="7e4f0-107">[in] Örneği belirtilen nesne sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="7e4f0-108">[in] Belirtilen nesne tarafından başvurulan nesne sayısını (diğer bir deyişle, içindeki öğelerin sayısını `objectRefIds` dizisi).</span><span class="sxs-lookup"><span data-stu-id="7e4f0-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="7e4f0-109">[in] Bir dizi tarafından başvurulan nesne kimliklerini `objectId`.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e4f0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e4f0-110">Remarks</span></span>  
 <span data-ttu-id="7e4f0-111">`ObjectReferences` Yöntemi yığınında bir çöp toplama tamamlandıktan sonra geri kalan her bir nesne için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="7e4f0-112">Profil Oluşturucu, bir hata bu geri çağrısından dönerse, profil oluşturma hizmetleri bu geri çağırma bir sonraki atık koleksiyonuna kadar devam etmeyecek.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="7e4f0-113">`ObjectReferences` Geri çağırma ile birlikte kullanılabilir [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) çalışma zamanı için bir tam nesne başvuru grafiği oluşturmak için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="7e4f0-114">Ortak dil çalışma zamanı (CLR) her nesne başvurusu tarafından yalnızca bir kez bildirilir sağlar `ObjectReferences` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="7e4f0-115">Tarafından döndürülen nesne kimlikleri `ObjectReferences` çöp toplama nesneleri taşıma ortasında olabileceğinden geri kendisini sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="7e4f0-116">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek kullanmamanız gerekir bir `ObjectReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="7e4f0-117">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında çöp toplama tamamlandığında ve İnceleme güvenli bir şekilde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="7e4f0-118">Bir null `ClassId` belirten `objectId` kaldırılıyor türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e4f0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e4f0-119">Requirements</span></span>  
 <span data-ttu-id="7e4f0-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e4f0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e4f0-121">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e4f0-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e4f0-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e4f0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e4f0-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e4f0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4f0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e4f0-124">See also</span></span>

- [<span data-ttu-id="7e4f0-125">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e4f0-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
