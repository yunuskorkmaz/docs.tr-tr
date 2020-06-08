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
ms.openlocfilehash: 17fbc99b30921f795c1f7ff882ec73432aade8c6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499252"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi

Doğrudan üye alan başvuruları ve bağımlılıklar aracılığıyla bu köklerin başvurduğu nesnelerin geçişli kapanışını tanımlar `ConditionalWeakTable` .

## <a name="syntax"></a>Söz dizimi

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
'ndaki `keyRefIds`, `valueRefIds` Ve `rootIds` dizilerindeki öğelerin sayısı.

`keyRefIds`\
'ndaki Her biri `ObjectID` bağımlı tanıtıcı çiftindeki birincil öğe için öğesini içeren bir nesne kimlikleri dizisi.

`valueRefIds`\
'ndaki Her biri `ObjectID` bağımlı tanıtıcı çiftindeki ikincil öğe için öğesini içeren bir nesne kimlikleri dizisi. ( `keyRefIds[i]` `valueRefIds[i]` canlı tutar.)

`rootIds`\
'ndaki `GCHandleID`Çöp toplama köküyle ilgili ek bilgiler içeren bir tamsayıyı işaret eden bir değer dizisi.

`ObjectID` `ConditionalWeakTableElementReferences` Çöp toplayıcı nesneleri eskileri yeni konumlara taşıma sürecinde olabileceğinden, yöntem tarafından döndürülen değerlerden hiçbiri geçerli değildir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `ConditionalWeakTableElementReferences` . `GarbageCollectionFinished`' De, tüm nesneler yeni konumlarına taşınmıştır ve denetleme yapılabilir.

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

.NET Framework 4,5 veya sonraki sürümler için bir profil oluşturucu [ICorProfilerCallback5](icorprofilercallback5-interface.md) arabirimini uygular ve yöntemi tarafından belirtilen bağımlılıkları kaydeder `ConditionalWeakTableElementReferences` . `ICorProfilerCallback5`, girdilere göre temsil edilen canlı nesneler arasındaki tüm bağımlılık kümesini sağlar `ConditionalWeakTable` . Bu bağımlılıklar ve [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) yöntemi tarafından belirtilen üye alanı başvuruları, canlı nesnelerin tam nesne grafiğini oluşturmak için yönetilen bir profil oluşturucuyu etkinleştirir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback5 Arabirimi](icorprofilercallback5-interface.md)
