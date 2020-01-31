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
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865967"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences Yöntemi
Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cRootRefs`  
 'ndaki `rootRefIds` dizisindeki başvuruların sayısı.  
  
 `rootRefIds`  
 'ndaki Bir statik nesneye veya yığındaki bir nesneye başvuran bir nesne kimlikleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil oluşturucuyu bildirmek için hem `RootReferences` hem de [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) çağrılır. Profil oluşturucular, normalde bir veya diğerini uygular, ancak `RootReferences2` geçirilen bilgiler, `RootReferences`geçirilen bir üst kümesidir.  
  
 `rootRefIds` dizisinin null bir nesne içermesi mümkündür. Örneğin, yığında bildirilen tüm nesne başvuruları çöp toplayıcı tarafından kök olarak değerlendirilir ve her zaman raporlanır.  
  
 Çöp toplama nesneleri eski adreslerden yeni adreslere taşıma işleminin ortasında olabileceğinden, `RootReferences` tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular `RootReferences` çağrısı sırasında nesneleri incelemeyi denememelidir. [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında tüm nesneler yeni konumlarına taşınır ve güvenle incelenebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
