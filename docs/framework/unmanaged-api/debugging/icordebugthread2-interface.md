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
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791426"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 Arabirimi
ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions Yöntemi](icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.|  
|[GetConnectionID Yöntemi](icordebugthread2-getconnectionid-method.md)|Bu `ICorDebugThread2`yönelik bir bağlantı tanımlayıcısı alır.|  
|[GetTaskID Yöntemi](icordebugthread2-gettaskid-method.md)|Bu `ICorDebugThread2`yönelik bir görev tanımlayıcısı alır.|  
|[GetVolatileOSThreadID Yöntemi](icordebugthread2-getvolatileosthreadid-method.md)|Bu `ICorDebugThread2`işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[InterceptCurrentException Yöntemi](icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
