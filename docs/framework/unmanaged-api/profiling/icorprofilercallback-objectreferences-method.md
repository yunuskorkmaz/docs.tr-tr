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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119255"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences Yöntemi
Profil Oluşturucu belirtilen nesne tarafından başvurulan nesneleri bellekte hakkında bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesnelere başvurma nesnesinin kimliği.  
  
 `classId`  
 [in] Örneği belirtilen nesne sınıfı kimliği.  
  
 `cObjectRefs`  
 [in] Belirtilen nesne tarafından başvurulan nesne sayısını (diğer bir deyişle, içindeki öğelerin sayısını `objectRefIds` dizisi).  
  
 `objectRefIds`  
 [in] Bir dizi tarafından başvurulan nesne kimliklerini `objectId`.  
  
## <a name="remarks"></a>Açıklamalar  
 `ObjectReferences` Yöntemi yığınında bir çöp toplama tamamlandıktan sonra geri kalan her bir nesne için çağrılır. Profil Oluşturucu, bir hata bu geri çağrısından dönerse, profil oluşturma hizmetleri bu geri çağırma bir sonraki atık koleksiyonuna kadar devam etmeyecek.  
  
 `ObjectReferences` Geri çağırma ile birlikte kullanılabilir [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) çalışma zamanı için bir tam nesne başvuru grafiği oluşturmak için geri çağırma. Ortak dil çalışma zamanı (CLR) her nesne başvurusu tarafından yalnızca bir kez bildirilir sağlar `ObjectReferences` yöntemi.  
  
 Tarafından döndürülen nesne kimlikleri `ObjectReferences` çöp toplama nesneleri taşıma ortasında olabileceğinden geri kendisini sırasında geçerli değildir. Bu nedenle, profil oluşturucular sırasında nesneleri incelemek kullanmamanız gerekir bir `ObjectReferences` çağırın. Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında çöp toplama tamamlandığında ve İnceleme güvenli bir şekilde gerçekleştirilebilir.  
  
 Bir null `ClassId` belirten `objectId` kaldırılıyor türüne sahip.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
