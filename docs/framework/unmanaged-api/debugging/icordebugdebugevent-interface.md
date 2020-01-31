---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: bef057bdb3ff0919337dd15f2d930159ddaf1bcf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783403"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent Arabirimi
Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventKind Yöntemi](icordebugdebugevent-geteventkind-method.md)|Bu `ICorDebugDebugEvent` nesnesinin ne tür bir olayın temsil ettiğini belirtir.|  
|[GetThread Yöntemi](icordebugdebugevent-getthread-method.md)|Olayın gerçekleştiği iş parçacığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:  
  
- [ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)  
  
- [Icordebugmoduledebugevent](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
