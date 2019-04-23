---
title: COR_DEBUG_STEP_RANGE Yapısı
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d7c3256d7b52a4e55dbb5bc420b0438983d2f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219687"
---
# <a name="cordebugsteprange-structure"></a>COR_DEBUG_STEP_RANGE Yapısı
Kod aralığı uzaklık bilgilerini içerir.  
  
 Bu yapı tarafından kullanılan [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`startOffset`|Aralığın başlangıç uzaklığı.|  
|`endOffset`|Aralığın uzaklığı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StepRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
