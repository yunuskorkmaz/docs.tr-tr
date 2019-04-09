---
title: CorDebugExceptionFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7b9b25673685dde8b75702c80f525515917ae1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078713"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags Numaralandırması
Bir özel durum hakkında ek bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Hiçbir özel durum söz konusudur.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|İnterceptable istisnadır.<br /><br /> Hata ayıklayıcı müdahale edemez, özel durumun zamanlamayı yine de olabilir. Örneğin, geçerli bir geri çağırma aşağıda Yönetilen kod yok ya da özel durum olayı just-ın-time (JIT) ekten sonuçlandı. özel durum müdahale edilebilir olamaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yeni değerler eklenebilir sonraki sürümlerinde bu sabit listesi için kullanan kodu hazırlamanız şekilde `CorDebugExceptionFlags` için beklenmeyen değer.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
