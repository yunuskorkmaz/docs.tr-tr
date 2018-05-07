---
title: Icordebugbreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugbreakpoint-interface1"></a>Icordebugbreakpoint Interface1
Bir kesme noktası bir işlevi veya izleme üzerine bir değeri temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Activate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Bu etkin durumunu ayarlar `ICorDebugBreakpoint`.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Gösteren bir değer alır olup olmadığını bu `ICorDebugBreakpoint` etkindir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kesme noktaları koşullu ifadeler doğrudan desteklemez. Bu tür işlevselliği isterseniz, bir hata ayıklayıcısı onu üstünde uygulamalıdır `ICorDebugBreakpoint`.  
  
 Icordebugfunctionbreakpoint arabirimi genişletiyor `ICorDebugBreakpoint` kesme noktaları işlevler içinde desteklemek için.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
