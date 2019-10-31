---
title: CorDebugIntercept Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 144bdb1b4e479c1e75f89911ad5002e2650e405d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098117"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept Numaralandırması
Ele geçirilebilecek kod türlerini gösterir (yani, ile).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`INTERCEPT_NONE`|Kod yakalanabilir.|  
|`INTERCEPT_CLASS_INIT`|Bir Oluşturucu yakalanabilir.|  
|`INTERCEPT_EXCEPTION_FILTER`|Özel durum filtresi yakalanabilir.|  
|`INTERCEPT_SECURITY`|Güvenliği zorlayan kod yakalanabilir.|  
|`INTERCEPT_CONTEXT_POLICY`|Bağlam ilkesi yakalanabilir.|  
|`INTERCEPT_INTERCEPTION`|Kullanılmadı.|  
|`INTERCEPT_ALL`|Tüm kod yakalanabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ele geçirilebilecek kod türlerini oluşturmak için [ICorDebugStepper:: Setyakatmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
