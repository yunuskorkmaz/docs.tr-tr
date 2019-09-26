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
ms.openlocfilehash: 11d5e2eb5e2743fca4876ed09add79be3eba514f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274201"
---
# <a name="cor_debug_step_range-structure"></a>COR_DEBUG_STEP_RANGE Yapısı
Bir kod aralığı için konum bilgilerini içerir.  
  
 Bu yapı, [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) yöntemi tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`startOffset`|Aralığın başındaki fark.|  
|`endOffset`|Aralığın sonundaki fark.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StepRange Yöntemi](icordebugstepper-steprange-method.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
