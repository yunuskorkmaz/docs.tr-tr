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
ms.openlocfilehash: 2d084ce0a785ba37c5b7dc937ed116cee74b7594
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720678"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="c255e-102">ICorProfilerCallback::RootReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c255e-102">ICorProfilerCallback::RootReferences Method</span></span>

<span data-ttu-id="c255e-103">Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="c255e-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c255e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c255e-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c255e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c255e-105">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="c255e-106">'ndaki Dizideki başvuruların sayısı `rootRefIds` .</span><span class="sxs-lookup"><span data-stu-id="c255e-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="c255e-107">'ndaki Bir statik nesneye veya yığındaki bir nesneye başvuran bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="c255e-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c255e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c255e-108">Remarks</span></span>  

 <span data-ttu-id="c255e-109">`RootReferences`Profil oluşturucuyu bildirmek için hem hem de [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c255e-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="c255e-110">Profil oluşturucular, normalde bir veya diğerini uygular, ancak geçirilen bilgiler `RootReferences2` geçilen bir üst kümesidir `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="c255e-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="c255e-111">`rootRefIds`Dizinin null bir nesne içermesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c255e-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="c255e-112">Örneğin, yığında bildirilen tüm nesne başvuruları çöp toplayıcı tarafından kök olarak değerlendirilir ve her zaman raporlanır.</span><span class="sxs-lookup"><span data-stu-id="c255e-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="c255e-113">Tarafından döndürülen nesne kimlikleri `RootReferences` geri çağırma sırasında geçerli değildir çünkü çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="c255e-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="c255e-114">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="c255e-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="c255e-115">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c255e-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c255e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c255e-116">Requirements</span></span>  

 <span data-ttu-id="c255e-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c255e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c255e-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c255e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c255e-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c255e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c255e-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c255e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c255e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c255e-121">See also</span></span>

- [<span data-ttu-id="c255e-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c255e-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
