---
title: ICorProfilerCallback2::GarbageCollectionStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: ed2553f2d971deefd85f731dd39f383cd096c5b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439819"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted Yöntemi
Çöp toplamanın başlattığı kod Profilcisi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cGenerations`  
 'ndaki `generationCollected` dizisindeki toplam girdi sayısı.  
  
 `generationCollected`  
 'ndaki Dizi dizinine karşılık gelen nesil bu çöp toplama tarafından toplanıyorsa `true` Boole değerleri dizisi. Aksi takdirde, `false`.  
  
 Dizi, oluşturmayı gösteren [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) numaralandırması değeri ile dizinlenir.  
  
 `reason`  
 'ndaki Çöp toplamanın oluşturulma nedenini gösteren [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çöp toplama ile ilgili tüm geri çağrılar `GarbageCollectionStarted` geri araması ile karşılık gelen [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması arasında gerçekleşmeyecektir. Bu geri aramalar aynı iş parçacığında gerçekleşmemelidir.  
  
 Profil oluşturucunun, `GarbageCollectionStarted` geri çağırma sırasında özgün konumlarında nesneleri incelemesi güvenlidir. Çöp toplayıcı, `GarbageCollectionStarted`dönüşden sonra nesneleri taşımaya başlayacaktır. Profil Oluşturucu bu geri aramadan çağrıldıktan sonra, profil oluşturucu, bir `ICorProfilerCallback2::GarbageCollectionFinished` geri çağırması alana kadar tüm nesne kimliklerini geçersiz hale getirmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
