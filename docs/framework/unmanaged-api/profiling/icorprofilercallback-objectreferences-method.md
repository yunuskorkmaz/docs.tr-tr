---
title: ICorProfilerCallback::ObjectReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866097"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences Yöntemi
Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 'ndaki Nesnelere başvuran nesnenin KIMLIĞI.  
  
 `classId`  
 'ndaki Belirtilen nesnenin bir örneği olduğu sınıfın KIMLIĞI.  
  
 `cObjectRefs`  
 'ndaki Belirtilen nesnenin başvurduğu nesne sayısı (yani `objectRefIds` dizideki öğelerin sayısı).  
  
 `objectRefIds`  
 'ndaki `objectId`tarafından başvurulan nesnelerin bir dizi kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir çöp toplama işlemi tamamlandıktan sonra yığında kalan her nesne için `ObjectReferences` yöntemi çağırılır. Profil Oluşturucu bu geri aramadan bir hata döndürürse, profil oluşturma hizmetleri sonraki atık toplamaya kadar bu geri aramayı çağırmayı sona erecek.  
  
 `ObjectReferences` geri çağırması [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) geri çağırması ile birlikte kullanılabilir ve çalışma zamanı için tamamen bir nesne başvurusu grafiği oluşturur. Ortak dil çalışma zamanı (CLR), her bir nesne başvurusunun `ObjectReferences` yöntemi tarafından yalnızca bir kez raporlanmasını sağlar.  
  
 Çöp toplama nesnelerin ortasında olabileceğinden, `ObjectReferences` tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular `ObjectReferences` çağrısı sırasında nesneleri incelemeyi denememelidir. [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında, çöp toplama tamamlanmıştır ve denetleme güvenle yapılabilir.  
  
 Null `ClassId`, `objectId`, kaldırma işlemi için bir türe sahip olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
