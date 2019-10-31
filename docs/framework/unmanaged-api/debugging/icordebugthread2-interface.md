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
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138674"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 Arabirimi
ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.|  
|[GetConnectionID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Bu `ICorDebugThread2`yönelik bir bağlantı tanımlayıcısı alır.|  
|[GetTaskID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Bu `ICorDebugThread2`yönelik bir görev tanımlayıcısı alır.|  
|[GetVolatileOSThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Bu `ICorDebugThread2`işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[InterceptCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
