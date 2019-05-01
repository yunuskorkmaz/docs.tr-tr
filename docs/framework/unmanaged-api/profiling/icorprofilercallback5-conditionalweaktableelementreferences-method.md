---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39ce72451f3a375f0cd3adb67a431162fc421a93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041608"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="85fe7-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85fe7-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="85fe7-103">Hem doğrudan üyesi alan başvuruları ve aracılığıyla bu kök tarafından başvurulan nesneleri geçişli kapatılmasını tanımlayan `ConditionalWeakTable` bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="85fe7-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="85fe7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85fe7-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="85fe7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85fe7-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="85fe7-106">[in] İçindeki öğelerin sayısını `keyRefIds`, `valueRefIds`, ve `rootIds` dizileri.</span><span class="sxs-lookup"><span data-stu-id="85fe7-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="85fe7-107">[in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı işleyici çiftinde birincil öğe için.</span><span class="sxs-lookup"><span data-stu-id="85fe7-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="85fe7-108">[in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı işleyici çifti ikincil öğe için.</span><span class="sxs-lookup"><span data-stu-id="85fe7-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="85fe7-109">(`keyRefIds[i]` tutar `valueRefIds[i]` Canlı.)</span><span class="sxs-lookup"><span data-stu-id="85fe7-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="85fe7-110">[in] Bir dizi `GCHandleID` üzerine çöp toplama kök hakkında ek bilgi içeren bir tamsayı değerleri.</span><span class="sxs-lookup"><span data-stu-id="85fe7-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="85fe7-111">Hiçbiri `ObjectID` tarafından döndürülen değerler `ConditionalWeakTableElementReferences` çöp toplayıcı nesnelerin yeni konumlarına eski geçme işleminde olabileceğinden yöntemi geri çağırma sırasındaki kendisini geçerli.</span><span class="sxs-lookup"><span data-stu-id="85fe7-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="85fe7-112">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ConditionalWeakTableElementReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="85fe7-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="85fe7-113">Adresindeki `GarbageCollectionFinished`tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme yapılması.</span><span class="sxs-lookup"><span data-stu-id="85fe7-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="85fe7-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="85fe7-114">Example</span></span>

<span data-ttu-id="85fe7-115">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir [Icorprofilercallback5](icorprofilercallback5-interface.md) ve bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="85fe7-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="85fe7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85fe7-116">Remarks</span></span>

<span data-ttu-id="85fe7-117">Bir profil oluşturucu için [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] veya üzeri sürümleri uygular [Icorprofilercallback5](icorprofilercallback5-interface.md) arabirimi ve kayıtları tarafından belirtilen bağımlılıkları `ConditionalWeakTableElementReferences` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85fe7-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="85fe7-118">`ICorProfilerCallback5` tarafından temsil edilen Canlı nesneler arasındaki bağımlılıklar kümesinin tamamını sunar `ConditionalWeakTable` girdileri.</span><span class="sxs-lookup"><span data-stu-id="85fe7-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="85fe7-119">Bu bağımlılıklar ve üye başvuruları tarafından belirtilen alan [Icorprofilercallback::objectreferences](icorprofilercallback-objectreferences-method.md) yöntemi Canlı nesnelerin tam nesne grafiği oluşturmak yönetilen profil oluşturucu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="85fe7-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="85fe7-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85fe7-120">Requirements</span></span>

<span data-ttu-id="85fe7-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85fe7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="85fe7-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85fe7-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="85fe7-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85fe7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="85fe7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85fe7-124">See also</span></span>

- [<span data-ttu-id="85fe7-125">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85fe7-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)