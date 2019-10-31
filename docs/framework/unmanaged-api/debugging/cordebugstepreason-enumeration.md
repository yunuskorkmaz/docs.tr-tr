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
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133681"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason Numaralandırması
Tek bir adımın sonucunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`STEP_NORMAL`|Adımlama, aynı işlev içinde normal şekilde tamamlandı.|  
|`STEP_RETURN`|İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.|  
|`STEP_CALL`|Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.|  
|`STEP_EXCEPTION_FILTER`|Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.|  
|`STEP_EXCEPTION_HANDLER`|Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.|  
|`STEP_INTERCEPT`|Denetim bir yakalayıcıyı geçti.|  
|`STEP_EXIT`|İş parçacığı, adım tamamlanmadan önce çıktı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StepComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
