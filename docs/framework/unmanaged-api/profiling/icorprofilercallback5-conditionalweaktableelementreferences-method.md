---
title: "ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback5.ConditionalWeakTableReferences
api_location: Mscorwks.dll
api_type: COM
f1_keywords: CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cfe86ac7d0cd5b4a5c6adb9f12ffe9577b6e611
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="c581b-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c581b-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>
<span data-ttu-id="c581b-103">Geçişli kapatma hem doğrudan üyesi alan başvuruları aracılığıyla ve aracılığıyla bu kökleri tarafından başvurulan nesne tanımlayan `ConditionalWeakTable` bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="c581b-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c581b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c581b-104">Syntax</span></span>  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c581b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c581b-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="c581b-106">[in] Öğe sayısı `keyRefIds`, `valueRefIds`, ve `rootIds` dizileri.</span><span class="sxs-lookup"><span data-stu-id="c581b-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>  
  
 `keyRefIds`  
 <span data-ttu-id="c581b-107">[in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı tanıtıcı çifti birincil öğe için.</span><span class="sxs-lookup"><span data-stu-id="c581b-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>  
  
 `valueRefIds`  
 <span data-ttu-id="c581b-108">[in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı tanıtıcı çifti ikincil öğe için.</span><span class="sxs-lookup"><span data-stu-id="c581b-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="c581b-109">(`keyRefIds[i]` tutar `valueRefIds[i]` Canlı.)</span><span class="sxs-lookup"><span data-stu-id="c581b-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>  
  
 `rootIds`  
 <span data-ttu-id="c581b-110">[in] Bir dizi `GCHandleID` atık toplama kök hakkında ek bilgi içeren bir tamsayı işaret değerleri.</span><span class="sxs-lookup"><span data-stu-id="c581b-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>  
  
 <span data-ttu-id="c581b-111">Hiçbiri `ObjectID` tarafından döndürülen değer `ConditionalWeakTableElementReferences` atık toplayıcı için yeni konumlar eski nesneleri taşıma işleminde olabileceğinden yöntemi geri çağırma sırasında kendisini geçerli.</span><span class="sxs-lookup"><span data-stu-id="c581b-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="c581b-112">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ConditionalWeakTableElementReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="c581b-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="c581b-113">Konumundaki `GarbageCollectionFinished`, tüm nesneler, yeni konumlarını taşınmıştır ve İnceleme yapılması.</span><span class="sxs-lookup"><span data-stu-id="c581b-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c581b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c581b-114">Example</span></span>  
 <span data-ttu-id="c581b-115">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) ve bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c581b-115">The following code example demonstrates how to implement [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) and use this method.</span></span>  
  
```  
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
  
## <a name="remarks"></a><span data-ttu-id="c581b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c581b-116">Remarks</span></span>  
 <span data-ttu-id="c581b-117">Profil Oluşturucu için [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] veya sonraki sürümleri uygulayan [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) arabirimi ve kayıtları tarafından belirtilen bağımlılıkları `ConditionalWeakTableElementReferences` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c581b-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="c581b-118">`ICorProfilerCallback5`tarafından temsil edilen Canlı nesneleri arasındaki bağımlılıkları tamamını sağlar `ConditionalWeakTable` girişleri.</span><span class="sxs-lookup"><span data-stu-id="c581b-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="c581b-119">Bu bağımlılıklar ve üye başvurular tarafından belirtilen alan [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) yöntemini etkinleştirmek Canlı nesnelerin tam nesne grafiği oluşturmak yönetilen bir profil oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="c581b-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c581b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c581b-120">Requirements</span></span>  
 <span data-ttu-id="c581b-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c581b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c581b-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c581b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c581b-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c581b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c581b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c581b-124">See Also</span></span>  
 [<span data-ttu-id="c581b-125">ICorProfilerCallback5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c581b-125">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
