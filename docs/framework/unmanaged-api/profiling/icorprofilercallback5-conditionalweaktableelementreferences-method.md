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
- CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad192f753cd1977c9ca68e147d23375ce092b66f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708239"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi
Hem doğrudan üyesi alan başvuruları ve aracılığıyla bu kök tarafından başvurulan nesneleri geçişli kapatılmasını tanımlayan `ConditionalWeakTable` bağımlılıkları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] İçindeki öğelerin sayısını `keyRefIds`, `valueRefIds`, ve `rootIds` dizileri.  
  
 `keyRefIds`  
 [in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı işleyici çiftinde birincil öğe için.  
  
 `valueRefIds`  
 [in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı işleyici çifti ikincil öğe için. (`keyRefIds[i]` tutar `valueRefIds[i]` Canlı.)  
  
 `rootIds`  
 [in] Bir dizi `GCHandleID` üzerine çöp toplama kök hakkında ek bilgi içeren bir tamsayı değerleri.  
  
 Hiçbiri `ObjectID` tarafından döndürülen değerler `ConditionalWeakTableElementReferences` çöp toplayıcı nesnelerin yeni konumlarına eski geçme işleminde olabileceğinden yöntemi geri çağırma sırasındaki kendisini geçerli. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ConditionalWeakTableElementReferences` çağırın. Adresindeki `GarbageCollectionFinished`tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme yapılması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) ve bu yöntemi kullanın.  
  
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
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu için [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] veya üzeri sürümleri uygular [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) arabirimi ve kayıtları tarafından belirtilen bağımlılıkları `ConditionalWeakTableElementReferences` yöntemi. `ICorProfilerCallback5` tarafından temsil edilen Canlı nesneler arasındaki bağımlılıklar kümesinin tamamını sunar `ConditionalWeakTable` girdileri. Bu bağımlılıklar ve üye başvuruları tarafından belirtilen alan [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) yöntemi Canlı nesnelerin tam nesne grafiği oluşturmak yönetilen profil oluşturucu etkinleştirin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
