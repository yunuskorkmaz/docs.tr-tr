---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback5:: ConditionalWeakTableElementReferences Yöntemi'
title: ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: ded43da029fe0b4c2a645823e62ca66b480f095c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760281"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="49119-103">ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49119-103">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="49119-104">Doğrudan üye alan başvuruları ve bağımlılıklar aracılığıyla bu köklerin başvurduğu nesnelerin geçişli kapanışını tanımlar `ConditionalWeakTable` .</span><span class="sxs-lookup"><span data-stu-id="49119-104">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="49119-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49119-105">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="49119-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49119-106">Parameters</span></span>

<span data-ttu-id="49119-107">`cRootRefs` 'ndaki `keyRefIds`, `valueRefIds` Ve `rootIds` dizilerindeki öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="49119-107">`cRootRefs` [in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

<span data-ttu-id="49119-108">`keyRefIds` 'ndaki Her biri `ObjectID` bağımlı tanıtıcı çiftindeki birincil öğe için öğesini içeren bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="49119-108">`keyRefIds` [in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

<span data-ttu-id="49119-109">`valueRefIds` 'ndaki Her biri `ObjectID` bağımlı tanıtıcı çiftindeki ikincil öğe için öğesini içeren bir nesne kimlikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="49119-109">`valueRefIds` [in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="49119-110">( `keyRefIds[i]` `valueRefIds[i]` canlı tutar.)</span><span class="sxs-lookup"><span data-stu-id="49119-110">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

<span data-ttu-id="49119-111">`rootIds` 'ndaki `GCHandleID` Çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="49119-111">`rootIds` [in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="49119-112">`ObjectID` `ConditionalWeakTableElementReferences` Çöp toplayıcı nesneleri eskileri yeni konumlara taşıma sürecinde olabileceğinden, yöntem tarafından döndürülen değerlerden hiçbiri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="49119-112">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="49119-113">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `ConditionalWeakTableElementReferences` .</span><span class="sxs-lookup"><span data-stu-id="49119-113">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="49119-114">`GarbageCollectionFinished`' De, tüm nesneler yeni konumlarına taşınmıştır ve denetleme yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="49119-114">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="49119-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="49119-115">Example</span></span>

<span data-ttu-id="49119-116">Aşağıdaki kod örneği, [ICorProfilerCallback5](icorprofilercallback5-interface.md) nasıl uygulanacağını ve bu yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49119-116">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a><span data-ttu-id="49119-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49119-117">Remarks</span></span>

<span data-ttu-id="49119-118">.NET Framework 4,5 veya sonraki sürümler için bir profil oluşturucu [ICorProfilerCallback5](icorprofilercallback5-interface.md) arabirimini uygular ve yöntemi tarafından belirtilen bağımlılıkları kaydeder `ConditionalWeakTableElementReferences` .</span><span class="sxs-lookup"><span data-stu-id="49119-118">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="49119-119">`ICorProfilerCallback5` , girdilere göre temsil edilen canlı nesneler arasındaki tüm bağımlılık kümesini sağlar `ConditionalWeakTable` .</span><span class="sxs-lookup"><span data-stu-id="49119-119">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="49119-120">Bu bağımlılıklar ve [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) yöntemi tarafından belirtilen üye alanı başvuruları, canlı nesnelerin tam nesne grafiğini oluşturmak için yönetilen bir profil oluşturucuyu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="49119-120">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="49119-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49119-121">Requirements</span></span>

<span data-ttu-id="49119-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49119-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="49119-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="49119-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="49119-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49119-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="49119-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49119-125">See also</span></span>

- [<span data-ttu-id="49119-126">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49119-126">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
