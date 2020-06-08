---
title: ICorProfilerCallback::RootReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: b587f30a01623c6e9806bcd9d01058a0880be239
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499915"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences Yöntemi
Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 'ndaki Dizideki başvuruların sayısı `rootRefIds` .  
  
 `rootRefIds`  
 'ndaki Bir statik nesneye veya yığındaki bir nesneye başvuran bir nesne kimlikleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `RootReferences`Profil oluşturucuyu bildirmek için hem hem de [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) çağırılır. Profil oluşturucular, normalde bir veya diğerini uygular, ancak geçirilen bilgiler `RootReferences2` geçilen bir üst kümesidir `RootReferences` .  
  
 `rootRefIds`Dizinin null bir nesne içermesi mümkündür. Örneğin, yığında bildirilen tüm nesne başvuruları çöp toplayıcı tarafından kök olarak değerlendirilir ve her zaman raporlanır.  
  
 Tarafından döndürülen nesne kimlikleri `RootReferences` geri çağırma sırasında geçerli değildir çünkü çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabilir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `RootReferences` . [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
