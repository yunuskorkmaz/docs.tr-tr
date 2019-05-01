---
title: CorGCReferenceType Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a673c98b11fbca5f66e9e1ae61f224448c20797
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966211"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType Sabit Listesi
Kaynağı olarak atık olarak toplanmış bir nesneyi tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`CorHandleStrong`|Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.|  
|`CorHandleStrongPinning`|Nesne işleyicisi tablosundan bir sabitlenmiş güçlü başvuru işleyici.|  
|`CorHandleWeakShort`|Nesne işleyicisi tablosundan bir tanıtıcı zayıf bir başvuru.|  
|`CorHandleWeakRefCount`|Nesne işleyicisi tablosundan bir tanıtıcı zayıf bir başvuru sayılan nesne.|  
|`CorHandleStrongRefCount`|Nesne işleyicisi tablosundan bir başvurusu sayılan nesne için tanıtıcı.|  
|`CorHandleStrongDependent`|Nesne işleyicisi tablosundan bir bağımlı nesne için tanıtıcı.|  
|`CorHandleStrongAsyncPinned`|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|`CorHandleStrongSizedByref`|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|`CorReferenceStack`|Yönetilen yığından başvuru.|  
|`CorReferenceFinalizer`|Sonlandırma sırasından bir başvuru.|  
|CorHandleStrongOnly|Yalnızca tanımlayıcı başvuruları, işleyici bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
|`CorHandleWeakOnly`|Zayıf başvurular yalnızca tanıtıcı bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
|`CorHandleAll`|Tüm başvuruları, işleyici bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorGCReferenceType` Numaralandırması şu şekilde kullanılır:  
  
- Değeri olarak `type` alanını [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) yapısı, başvuru veya tanıtıcısı kaynağını gösterir.  
  
- Olarak `types` bağımsız değişkeni [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yöntemi numaralandırmada içerecek şekilde tanıtıcıları türlerini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
