---
title: ICorDebugBreakpoint Arabirimi
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
ms.openlocfilehash: a7e454c15ddfa977a6d06921a5d80a6c05dca92f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973580"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint Arabirimi

Bir kesme noktası bir işlev veya bir izleme noktasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Activate Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Bu etkin durumunu ayarlar `ICorDebugBreakpoint`.|  
|[IsActive Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Belirten bir değer alır olup bu `ICorDebugBreakpoint` etkindir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kesme noktaları, koşullu ifadeleri doğrudan desteklemez. Bu işlevselliğin isterseniz, bir hata ayıklayıcı, üst kısmındaki uygulamalıdır `ICorDebugBreakpoint`.  
  
 Icordebugfunctionbreakpoint arabirimi genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
