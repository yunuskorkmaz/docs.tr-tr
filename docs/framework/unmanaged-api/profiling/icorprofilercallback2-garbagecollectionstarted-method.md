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
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499811"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted Yöntemi
Çöp toplamanın başlattığı kod Profilcisi bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cGenerations`  
 'ndaki Dizideki toplam girdi sayısı `generationCollected` .  
  
 `generationCollected`  
 'ndaki `true`Dizi dizinine karşılık gelen nesil bu çöp toplama tarafından toplanıyorsa bir Boole değeri dizisi; Aksi takdirde, `false` .  
  
 Dizi, oluşturmayı gösteren [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) numaralandırması değeri ile dizinlenir.  
  
 `reason`  
 'ndaki Çöp toplamanın oluşturulma nedenini gösteren [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu çöp toplama ile ilgili tüm geri çağrılar, `GarbageCollectionStarted` geri çağırma ve karşılık gelen [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması arasında gerçekleşmeyecektir. Bu geri aramalar aynı iş parçacığında gerçekleşmemelidir.  
  
 Profil oluşturucunun geri çağırma sırasında özgün konumlarında nesneleri incelemesi güvenlidir `GarbageCollectionStarted` . Çöp toplayıcı, öğesinden dönüşten sonra nesneleri taşımaya başlayacaktır `GarbageCollectionStarted` . Profil Oluşturucu bu geri aramadan çağrıldıktan sonra, profil oluşturucu, bir geri arama alıncaya kadar tüm nesne kimliklerini geçersiz hale getirmelidir `ICorProfilerCallback2::GarbageCollectionFinished` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
