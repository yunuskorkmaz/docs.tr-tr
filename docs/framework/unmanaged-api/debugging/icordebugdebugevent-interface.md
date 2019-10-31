---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137034"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent Arabirimi
Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventKind Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|Bu `ICorDebugDebugEvent` nesnesinin ne tür bir olayın temsil ettiğini belirtir.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Olayın gerçekleştiği iş parçacığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:  
  
- [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [Icordebugmoduledebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
