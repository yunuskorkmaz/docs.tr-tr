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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199940"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept Numaralandırması
(Bu, içine girdiğiniz olduğu gibi), geçirilebilir kod türlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`INTERCEPT_NONE`|Kod geçirilebilir.|  
|`INTERCEPT_CLASS_INIT`|Bir oluşturucu geçirilebilir.|  
|`INTERCEPT_EXCEPTION_FILTER`|Özel Durum Filtresi geçirilebilir.|  
|`INTERCEPT_SECURITY`|Güvenlik uygulayan kod ele geçirilebilir.|  
|`INTERCEPT_CONTEXT_POLICY`|Bir bağlam ilke geçirilebilir.|  
|`INTERCEPT_INTERCEPTION`|Kullanılmadı.|  
|`INTERCEPT_ALL`|Tüm kod geçirilebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [ICorDebugStepper::setınterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) geçirilebilir kod türlerini oluşturmak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
