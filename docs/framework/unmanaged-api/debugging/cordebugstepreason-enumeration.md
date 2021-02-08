---
description: 'Daha fazla bilgi edinin: CorDebugStepReason numaralandırması'
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
ms.openlocfilehash: 2a331b09709ffb6179f2e481baf4bf421d60ea99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801546"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason Numaralandırması

Tek bir adımın sonucunu gösterir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`STEP_NORMAL`|Adımlama, aynı işlev içinde normal şekilde tamamlandı.|  
|`STEP_RETURN`|İşlev çağrıldıktan sonra normal şekilde çalışmaya devam eder.|  
|`STEP_CALL`|Yeni çağrılan bir işlevin başlangıcında, Adımlama normal şekilde devam eder.|  
|`STEP_EXCEPTION_FILTER`|Bir özel durum oluşturuldu ve denetim bir özel durum filtresine geçirildi.|  
|`STEP_EXCEPTION_HANDLER`|Özel durum oluşturuldu ve denetim özel durum işleyicisine geçirildi.|  
|`STEP_INTERCEPT`|Denetim bir yakalayıcıyı geçti.|  
|`STEP_EXIT`|İş parçacığı, adım tamamlanmadan önce çıktı.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StepComplete Yöntemi](icordebugmanagedcallback-stepcomplete-method.md)
- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
