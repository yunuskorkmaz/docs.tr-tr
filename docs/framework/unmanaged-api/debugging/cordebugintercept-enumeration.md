---
title: "CorDebugIntercept Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 814ee1285780d5a3b02aa5926ad4628e339a9114
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept Numaralandırması
Tür (yani içine adım adım olan), geçirilebilir kod gösterir.  
  
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
|`INTERCEPT_EXCEPTION_FILTER`|Bir özel durum filtresi geçirilebilir.|  
|`INTERCEPT_SECURITY`|Güvenlik uygulayan kod ele geçirilebilir.|  
|`INTERCEPT_CONTEXT_POLICY`|Bir bağlam İlkesi geçirilebilir.|  
|`INTERCEPT_INTERCEPTION`|Kullanılmadı.|  
|`INTERCEPT_ALL`|Tüm kod geçirilebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [ICorDebugStepper::setınterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) geçirilebilir kod türlerini kurmaya yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
