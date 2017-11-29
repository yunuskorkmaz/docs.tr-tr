---
title: ICorDebugRegisterSet Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet Arabirimi
Yazmaçları kod şu anda yürütülmekte bilgisayarda kullanılabilir kümesini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.|  
|[GetRegistersAvailable yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Alır bir bit maskesi bu kayıtları belirten `ICorDebugRegisterSet` şu anda kullanılabilir.|  
|[GetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Geçerli iş parçacığının bağlamını alır.|  
|[SetRegisters yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|.NET Framework sürüm 2.0 uygulanmadı.|  
|[SetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2.0 uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRegisterSet` Arabirimi yalnızca 32-bit kayıtlarını destekler. Kullanım [Icordebugregisterset2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) platformlarda ek kayıtları gerektiren IA-64 gibi arabirimi.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Icordebugregisterset2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
