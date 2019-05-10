---
title: ICorDebugDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 013cdfbb6a2904e60d6f7b4df6d40e3d65606fcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606824"
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
  
- [Icordebugexceptiondebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [Icordebugmoduledebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
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
