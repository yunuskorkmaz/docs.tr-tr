---
description: ': ICorProfilerCallback:: RootReferences Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e09434c425784e646c9856693abdfd4ac0d49273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788872"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="92af5-103">ICorProfilerCallback::RootReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92af5-103">ICorProfilerCallback::RootReferences Method</span></span>

<span data-ttu-id="92af5-104">Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="92af5-104">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92af5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92af5-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="92af5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92af5-106">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="92af5-107">'ndaki Dizideki başvuruların sayısı `rootRefIds` .</span><span class="sxs-lookup"><span data-stu-id="92af5-107">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="92af5-108">'ndaki Bir statik nesneye veya yığındaki bir nesneye başvuran bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="92af5-108">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92af5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92af5-109">Remarks</span></span>  

 <span data-ttu-id="92af5-110">`RootReferences`Profil oluşturucuyu bildirmek için hem hem de [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) çağırılır.</span><span class="sxs-lookup"><span data-stu-id="92af5-110">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="92af5-111">Profil oluşturucular, normalde bir veya diğerini uygular, ancak geçirilen bilgiler `RootReferences2` geçilen bir üst kümesidir `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="92af5-111">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="92af5-112">`rootRefIds`Dizinin null bir nesne içermesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="92af5-112">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="92af5-113">Örneğin, yığında bildirilen tüm nesne başvuruları çöp toplayıcı tarafından kök olarak değerlendirilir ve her zaman raporlanır.</span><span class="sxs-lookup"><span data-stu-id="92af5-113">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="92af5-114">Tarafından döndürülen nesne kimlikleri `RootReferences` geri çağırma sırasında geçerli değildir çünkü çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="92af5-114">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="92af5-115">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="92af5-115">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="92af5-116">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="92af5-116">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92af5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92af5-117">Requirements</span></span>  

 <span data-ttu-id="92af5-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92af5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92af5-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92af5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92af5-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92af5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92af5-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92af5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92af5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92af5-122">See also</span></span>

- [<span data-ttu-id="92af5-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92af5-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
