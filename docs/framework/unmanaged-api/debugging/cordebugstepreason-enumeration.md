---
title: CorDebugStepReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723166"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason Numaralandırması
Bir adımın sonucunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`STEP_NORMAL`|Adımlama, normalde, aynı işlevin içinde tamamlandı.|  
|`STEP_RETURN`|İşlev sonra Adımlama normal olarak devam.|  
|`STEP_CALL`|Adımlama normalde, yeni çağrılan bir işlevin başında devam eder.|  
|`STEP_EXCEPTION_FILTER`|Bir özel durum oluşturuldu ve özel durum filtresi için denetimi geçildi.|  
|`STEP_EXCEPTION_HANDLER`|Bir özel durum oluşturuldu ve bir özel durum işleyicisine denetimi geçildi.|  
|`STEP_INTERCEPT`|Denetim için bir dinleyiciyi geçirildi.|  
|`STEP_EXIT`|İş parçacığı adımı tamamlanmadan önce çıkıldı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StepComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
