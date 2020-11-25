---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: d73857bd9d0d5dd9e5eff0c89dcc573ae0d93f0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731884"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent Arabirimi

Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventKind Yöntemi](icordebugdebugevent-geteventkind-method.md)|Bu nesnenin ne tür bir olayın `ICorDebugDebugEvent` temsil ettiğini belirtir.|  
|[GetThread Yöntemi](icordebugdebugevent-getthread-method.md)|Olayın gerçekleştiği iş parçacığını alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki arabirimler `ICorDebugDebugEvent` arabiriminden türetilir:  
  
- [ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)  
  
- [Icordebugmoduledebugevent](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. `QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
