---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550cb6379ef0d5d17a3446b3f21120208b5a3dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110194"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent Arabirimi
Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventKind Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.|  
|[GetThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|Olayın gerçekleştiği iş parçacığı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki arabirimlerinden türetilmiştir `ICorDebugDebugEvent` arabirimi:  
  
-   [Icordebugexceptiondebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [Icordebugmoduledebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  Arabirimi yalnızca .NET Native ile kullanılabilir. Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
