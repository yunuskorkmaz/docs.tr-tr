---
title: "ICorProfilerCallback::RootReferences Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd057538450deeb46a72178c725103e04a8dd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="94d52-102">ICorProfilerCallback::RootReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94d52-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="94d52-103">Profil Oluşturucu çöp toplamadan sonra kök başvurular hakkındaki bilgilerle bildirir.</span><span class="sxs-lookup"><span data-stu-id="94d52-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94d52-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94d52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94d52-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="94d52-106">[in] Başvuruları sayısı `rootRefIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="94d52-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="94d52-107">[in] Statik bir nesne veya yığında bir nesne başvuru nesnesi kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="94d52-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d52-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94d52-108">Remarks</span></span>  
 <span data-ttu-id="94d52-109">Her ikisi de `RootReferences` ve [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) profil oluşturucu bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="94d52-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="94d52-110">Profil oluşturucular normalde uygulamak birini veya diğerini, ancak ikisi birden değil, bilgileri geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="94d52-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="94d52-111">Mümkündür `rootRefIds` dizi null bir nesne içeriyor.</span><span class="sxs-lookup"><span data-stu-id="94d52-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="94d52-112">Örneğin, yığında bildirilen tüm nesne başvuruları kökleri atık toplayıcısı tarafından kabul edilir ve her zaman bildirilir.</span><span class="sxs-lookup"><span data-stu-id="94d52-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="94d52-113">Tarafından döndürülen nesne kimlikleri `RootReferences` çöp toplama nesneleri eski adreslerinden yeni adreslere taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="94d52-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="94d52-114">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="94d52-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="94d52-115">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesneleri yeni konumlarına taşınır ve güvenli bir şekilde Denetlenmekte.</span><span class="sxs-lookup"><span data-stu-id="94d52-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d52-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94d52-116">Requirements</span></span>  
 <span data-ttu-id="94d52-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94d52-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d52-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94d52-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94d52-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94d52-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94d52-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94d52-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d52-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94d52-121">See Also</span></span>  
 [<span data-ttu-id="94d52-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94d52-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
