---
title: "ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4adeda7ac884b37bcfc2b0c9599dd8e36c469747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="d6d1e-102">ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6d1e-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="d6d1e-103">Profil Oluşturucu en son çöp toplamadan beri oluşturulan her belirtilen sınıf örneklerini sayısı hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6d1e-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6d1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6d1e-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="d6d1e-106">[in] Boyutunu `classIds` ve `cObjects` dizileri.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="d6d1e-107">[in] Bir dizi sınıfının kimlikleri, burada her kimliği ile bir veya daha fazla örnekleri bir sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="d6d1e-108">[in] Dizisi burada her tamsayı belirtir, karşılık gelen sınıf için örnek sayısı, `classIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6d1e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6d1e-109">Remarks</span></span>  
 <span data-ttu-id="d6d1e-110">`classIds` Ve `cObjects` paralel diziler dizidir.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="d6d1e-111">Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıf başvurusu.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="d6d1e-112">Bir sınıf örneği önceki çöp toplamadan beri oluşturulduysa sınıfı atlanır.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="d6d1e-113">`ObjectsAllocatedByClass` Geri çağırma büyük nesne yığın ayrılmış nesneleri bildirmez.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="d6d1e-114">Sayıları tarafından bildirilen `ObjectsAllocatedByClass` yalnızca tahminleri.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="d6d1e-115">Tam sayılar için kullanmak [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="d6d1e-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="d6d1e-116">`classIds` Dizisi, bir veya daha fazla null girdiler içerebilir, varsa karşılık gelen `cObjects` dizi kaldırılması türü içerir.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6d1e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6d1e-117">Requirements</span></span>  
 <span data-ttu-id="d6d1e-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6d1e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6d1e-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6d1e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6d1e-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6d1e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6d1e-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6d1e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d1e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6d1e-122">See Also</span></span>  
 [<span data-ttu-id="d6d1e-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6d1e-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
