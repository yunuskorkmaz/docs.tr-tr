---
description: 'Daha fazla bilgi edinin: ICorDebugThread2 Interface'
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
ms.openlocfilehash: 81f687f6daff9ffa7298ec6d818a214b8934bcc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658509"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 Arabirimi

ICorDebugThread arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions Yöntemi](icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçevelerinden etkin işlevlerle ilgili verileri içeren COR_ACTIVE_FUNCTION örneklerinin bir dizisini alır.|  
|[GetConnectionID Yöntemi](icordebugthread2-getconnectionid-method.md)|Bunun için bir bağlantı tanımlayıcısı alır `ICorDebugThread2` .|  
|[GetTaskID Yöntemi](icordebugthread2-gettaskid-method.md)|Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2` .|  
|[GetVolatileOSThreadID Yöntemi](icordebugthread2-getvolatileosthreadid-method.md)|Bunun için işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2` .|  
|[InterceptCurrentException Yöntemi](icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcının bir iş parçacığında geçerli özel durumu ele almasına izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
