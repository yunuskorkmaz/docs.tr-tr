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
ms.openlocfilehash: 4ee3c3302d77bcc7b807c01ccb5bab172153ddda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences Yöntemi
Geçişli kapatma hem doğrudan üyesi alan başvuruları aracılığıyla ve aracılığıyla bu kökleri tarafından başvurulan nesne tanımlayan `ConditionalWeakTable` bağımlılıkları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 [in] Öğe sayısı `keyRefIds`, `valueRefIds`, ve `rootIds` dizileri.  
  
 `keyRefIds`  
 [in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı tanıtıcı çifti birincil öğe için.  
  
 `valueRefIds`  
 [in] Her biri içeren bir dizi nesne kimlikleri `ObjectID` bağımlı tanıtıcı çifti ikincil öğe için. (`keyRefIds[i]` tutar `valueRefIds[i]` Canlı.)  
  
 `rootIds`  
 [in] Bir dizi `GCHandleID` atık toplama kök hakkında ek bilgi içeren bir tamsayı işaret değerleri.  
  
 Hiçbiri `ObjectID` tarafından döndürülen değer `ConditionalWeakTableElementReferences` atık toplayıcı için yeni konumlar eski nesneleri taşıma işleminde olabileceğinden yöntemi geri çağırma sırasında kendisini geçerli. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `ConditionalWeakTableElementReferences` çağırın. Konumundaki `GarbageCollectionFinished`, tüm nesneler, yeni konumlarını taşınmıştır ve İnceleme yapılması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) ve bu yöntemi kullanın.  
  
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
 Profil Oluşturucu için [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] veya sonraki sürümleri uygulayan [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) arabirimi ve kayıtları tarafından belirtilen bağımlılıkları `ConditionalWeakTableElementReferences` yöntemi. `ICorProfilerCallback5` tarafından temsil edilen Canlı nesneleri arasındaki bağımlılıkları tamamını sağlar `ConditionalWeakTable` girişleri. Bu bağımlılıklar ve üye başvurular tarafından belirtilen alan [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) yöntemini etkinleştirmek Canlı nesnelerin tam nesne grafiği oluşturmak yönetilen bir profil oluşturucu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
