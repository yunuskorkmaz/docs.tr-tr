---
title: ICorDebugThread3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137499"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 Arabirimi
[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStackWalk Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi oluşturur.|  
|[GetActiveInternalFrames Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|Yığında iç çerçeveler ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugThread3`, ICorDebugThread arabirimine yönelik bir mantıksal uzantıdır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
