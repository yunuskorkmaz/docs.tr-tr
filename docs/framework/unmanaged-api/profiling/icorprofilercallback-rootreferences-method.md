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
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865967"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="a62c4-102">ICorProfilerCallback::RootReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a62c4-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="a62c4-103">Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="a62c4-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a62c4-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a62c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a62c4-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="a62c4-106">'ndaki `rootRefIds` dizisindeki başvuruların sayısı.</span><span class="sxs-lookup"><span data-stu-id="a62c4-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="a62c4-107">'ndaki Bir statik nesneye veya yığındaki bir nesneye başvuran bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="a62c4-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a62c4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a62c4-108">Remarks</span></span>  
 <span data-ttu-id="a62c4-109">Profil oluşturucuyu bildirmek için hem `RootReferences` hem de [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a62c4-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="a62c4-110">Profil oluşturucular, normalde bir veya diğerini uygular, ancak `RootReferences2` geçirilen bilgiler, `RootReferences`geçirilen bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="a62c4-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="a62c4-111">`rootRefIds` dizisinin null bir nesne içermesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a62c4-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="a62c4-112">Örneğin, yığında bildirilen tüm nesne başvuruları çöp toplayıcı tarafından kök olarak değerlendirilir ve her zaman raporlanır.</span><span class="sxs-lookup"><span data-stu-id="a62c4-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="a62c4-113">Çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabileceğinden, `RootReferences` tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="a62c4-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="a62c4-114">Bu nedenle, profil oluşturucular `RootReferences` çağrısı sırasında nesneleri incelemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="a62c4-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="a62c4-115">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="a62c4-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62c4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a62c4-116">Requirements</span></span>  
 <span data-ttu-id="a62c4-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a62c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62c4-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a62c4-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a62c4-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a62c4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a62c4-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62c4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a62c4-121">See also</span></span>

- [<span data-ttu-id="a62c4-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a62c4-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
