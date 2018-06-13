---
title: ICorProfilerCallback::RootReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 467d065ab4d47e698c7043697ebe2ccf5f98a3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452591"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="2d989-102">ICorProfilerCallback::RootReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d989-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="2d989-103">Profil Oluşturucu çöp toplamadan sonra kök başvurular hakkındaki bilgilerle bildirir.</span><span class="sxs-lookup"><span data-stu-id="2d989-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d989-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d989-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d989-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d989-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="2d989-106">[in] Başvuruları sayısı `rootRefIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="2d989-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="2d989-107">[in] Statik bir nesne veya yığında bir nesne başvuru nesnesi kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="2d989-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d989-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d989-108">Remarks</span></span>  
 <span data-ttu-id="2d989-109">Her ikisi de `RootReferences` ve [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) profil oluşturucu bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2d989-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="2d989-110">Profil oluşturucular normalde uygulamak birini veya diğerini, ancak ikisi birden değil, bilgileri geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="2d989-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="2d989-111">Mümkündür `rootRefIds` dizi null bir nesne içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2d989-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="2d989-112">Örneğin, yığında bildirilen tüm nesne başvuruları kökleri atık toplayıcısı tarafından kabul edilir ve her zaman bildirilir.</span><span class="sxs-lookup"><span data-stu-id="2d989-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="2d989-113">Tarafından döndürülen nesne kimlikleri `RootReferences` çöp toplama nesneleri eski adreslerinden yeni adreslere taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2d989-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="2d989-114">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="2d989-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="2d989-115">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesneleri yeni konumlarına taşınır ve güvenli bir şekilde Denetlenmekte.</span><span class="sxs-lookup"><span data-stu-id="2d989-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d989-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d989-116">Requirements</span></span>  
 <span data-ttu-id="2d989-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d989-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d989-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d989-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d989-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d989-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d989-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d989-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d989-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d989-121">See Also</span></span>  
 [<span data-ttu-id="2d989-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d989-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
