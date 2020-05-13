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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379826"
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
