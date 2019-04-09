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
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153939"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 Arabirimi
Icordebugthread arabirimi mantıksal uzantısı olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçeveler etkin işlevler hakkında veri içeren cor_actıve_functıon örnekleri dizisini alır.|  
|[GetConnectionID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Bunun için bir bağlantı tanımlayıcısını alır `ICorDebugThread2`.|  
|[GetTaskID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Bunun için bir görev tanımlayıcısını alır `ICorDebugThread2`.|  
|[GetVolatileOSThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Bu işletim sistemi iş parçacığı tanıtıcısını alır `ICorDebugThread2`.|  
|[InterceptCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcı bir iş parçacığında geçerli özel durumun izlemesine izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
