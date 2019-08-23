---
title: ICorDebugThread2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d21c221bba3ac668924003f96580bb660229ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962999"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 Arabirimi
ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.|  
|[GetConnectionID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Bunun `ICorDebugThread2`için bir bağlantı tanımlayıcısı alır.|  
|[GetTaskID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Bunun `ICorDebugThread2`için bir görev tanımlayıcısı alır.|  
|[GetVolatileOSThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Bunun `ICorDebugThread2`için işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[InterceptCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
