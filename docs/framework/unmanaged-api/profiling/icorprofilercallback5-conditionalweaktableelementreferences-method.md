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
ms.openlocfilehash: ad721d28f6a7dc6ae0370ce10178990cb02fb9f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430057"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi

Doğrudan üye alan başvuruları ve `ConditionalWeakTable` bağımlılıklarıyla, bu köklerin başvurduğu nesnelerin geçişli kapatılmasını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Parametreler

`cRootRefs`\
'ndaki `keyRefIds`, `valueRefIds`ve `rootIds` dizilerindeki öğe sayısı.

`keyRefIds`\
'ndaki Her biri bağımlı tanıtıcı çiftindeki birincil öğe için `ObjectID` içeren bir nesne kimlikleri dizisi.

`valueRefIds`\
'ndaki Her biri bağımlı tanıtıcı çiftindeki ikincil öğe için `ObjectID` içeren bir nesne kimlikleri dizisi. (`keyRefIds[i]` `valueRefIds[i]` canlı tutar.)

`rootIds`\
'ndaki Çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden `GCHandleID` değerleri dizisi.

Çöp toplayıcı nesneleri eskileri yeni konumlara taşıma sürecinde olabileceğinden, `ConditionalWeakTableElementReferences` yöntemi tarafından döndürülen `ObjectID` değerlerinden hiçbiri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular `ConditionalWeakTableElementReferences` çağrısı sırasında nesneleri incelemeyi denememelidir. `GarbageCollectionFinished`, tüm nesneler yeni konumlarına taşınmıştır ve denetleme yapılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, [ICorProfilerCallback5](icorprofilercallback5-interface.md) nasıl uygulanacağını ve bu yöntemin nasıl kullanılacağını gösterir.

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

## <a name="remarks"></a>Açıklamalar

.NET Framework 4,5 veya sonraki sürümler için bir profil oluşturucu [ICorProfilerCallback5](icorprofilercallback5-interface.md) arabirimini uygular ve `ConditionalWeakTableElementReferences` yöntemi tarafından belirtilen bağımlılıkları kaydeder. `ICorProfilerCallback5`, `ConditionalWeakTable` girdileri tarafından temsil edilen canlı nesneler arasındaki tüm bağımlılık kümesini sağlar. Bu bağımlılıklar ve [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) yöntemi tarafından belirtilen üye alanı başvuruları, canlı nesnelerin tam nesne grafiğini oluşturmak için yönetilen bir profil oluşturucuyu etkinleştirir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback5 Arabirimi](icorprofilercallback5-interface.md)
