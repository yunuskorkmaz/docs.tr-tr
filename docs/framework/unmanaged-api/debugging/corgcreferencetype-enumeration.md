---
title: CorGCReferenceType Sabit Listesi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45ca1e9c6123a4b22a1645d151e49a0dd65addbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType Sabit Listesi
Çöp toplanan olması için bir nesne kaynak tanımlar.  
  
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
|`CorHandleStrongPinning`|Sabitlenmiş güçlü bir başvuru için bir tanıtıcı nesnesi tanıtıcı tablosundan.|  
|`CorHandleWeakShort`|Zayıf başvuru için bir tanıtıcı nesnesi tanıtıcı tablosundan.|  
|`CorHandleWeakRefCount`|Zayıf başvuruları sayılan nesnesi için tanıtıcı nesnesi tanıtıcı tablosundan.|  
|`CorHandleStrongRefCount`|Başvuruları sayılan nesnesi için bir tanıtıcı nesnesi tanıtıcı tablosundan.|  
|`CorHandleStrongDependent`|Bağımlı bir nesne için bir tanıtıcı nesnesi tanıtıcı tablosundan.|  
|`CorHandleStrongAsyncPinned`|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|`CorHandleStrongSizedByref`|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|`CorReferenceStack`|Yönetilen yığın bir başvuru.|  
|`CorReferenceFinalizer`|Sonlandırıcı sırasından başvuru.|  
|CorHandleStrongOnly|Yalnızca güçlü başvurular tanıtıcısı bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
|`CorHandleWeakOnly`|Yalnızca zayıf başvurular tanıtıcısı bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
|`CorHandleAll`|Tüm başvuruları tanıtıcısı bir tablo döndürür. Bu değer tarafından kullanılan [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yalnızca yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorGCReferenceType` Numaralandırma aşağıdaki gibi kullanılır:  
  
-   Değeri olarak `type` alanını [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) yapısı, başvuru veya tanıtıcı kaynağını gösterir.  
  
-   Olarak `types` bağımsız değişkeni [Icordebugprocess5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) yöntemi, numaralandırmada içerecek şekilde tanıtıcıları türlerini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
