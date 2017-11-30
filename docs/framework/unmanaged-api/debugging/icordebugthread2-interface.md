---
title: Icordebugthread2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a>Icordebugthread2 Interface1
Icordebugthread arabirimi için mantıksal bir uzantısı olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetActiveFunctions yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|Bir iş parçacığının çerçeveleri etkin işlevlerde ilgili verileri içeren cor_actıve_functıon örnekleri dizisi alır.|  
|[Getconnectionıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|Bunun için bir bağlantı tanımlayıcı alır `ICorDebugThread2`.|  
|[Gettaskıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|Bunun için bir görev tanımlayıcısı alır `ICorDebugThread2`.|  
|[Getvolatileosthreadıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|Bu işletim sistemi iş parçacığı tanımlayıcısını alır `ICorDebugThread2`.|  
|[Interceptcurrentexception yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|Bir hata ayıklayıcısı geçerli özel durumun bir iş parçacığında izlemesine izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
