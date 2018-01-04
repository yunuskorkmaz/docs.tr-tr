---
title: "ICorProfilerCallback2::GarbageCollectionStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b721b990312f9acda5c9e0208f998793735d2cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted Yöntemi
Kod profil oluşturucu çöp toplama başlatıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cGenerations`  
 [in] Toplam sayısı giriş `generationCollected` dizi.  
  
 `generationCollected`  
 [in] Boole değerleri olan bir dizi `true` dizi dizini karşılık gelen oluşturma, bu atık toplama tarafından toplanan Aksi takdirde `false`.  
  
 Dizi değeri tarafından dizine [cor_prf_gc_generatıon](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) nesli belirten numaralandırma.  
  
 `reason`  
 [in] Değerini [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) çöp toplama nedenini belirten numaralandırma kopyaladığınızda.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çöp toplama ilgilidir tüm geri aramalar arasında gerçekleşecek `GarbageCollectionStarted` geri çağırma ve karşılık gelen [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırma. Bu geri aramalar aynı iş parçacığı üzerinde meydana değil.  
  
 Nesneleri özgün konumlarına sırasında incelemek profil oluşturucu güvenlidir `GarbageCollectionStarted` geri çağırma. Çöp toplayıcı dönüş sonra taşıma nesneleri başlar `GarbageCollectionStarted`. Profil Oluşturucu bu geri aramasından döndürdü sonra Profil Oluşturucu aldığı kadar geçersiz olduğu tüm nesne kimlikleri dikkate almanız gereken bir `ICorProfilerCallback2::GarbageCollectionFinished` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
