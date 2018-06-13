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
ms.openlocfilehash: d963a478ee7ae42159a0eb8a4b41cf20ae663aa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405463"
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
|`DEBUG_EXCEPTION_NONE`|Hiçbir özel durum yoktur.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Özel durum interceptable kullanılır.<br /><br /> Hata ayıklayıcı müdahale edemez şekilde özel zamanlama hala olabilir. Örneğin, yönetilen kodu geçerli geri çağırma aşağıda yok veya tam zamanında (JIT) ekten özel durum olayı sonuçlandı, özel durum ele geçirilebilecek olamaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yeni değerler eklenebilir sonraki sürümlerinde, bu numaralandırma için kullanan kodu hazırlamalısınız şekilde `CorDebugExceptionFlags` için beklenmeyen değer.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
