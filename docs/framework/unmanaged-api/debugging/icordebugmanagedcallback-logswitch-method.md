---
title: "ICorDebugManagedCallback::LogSwitch Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: beb4dc25d634f64d8740005abf83e51ec1e3e731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch Yöntemi
Hata ayıklayıcı ortak dil çalışma zamanı (CLR) yönetilen iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.Switch> sınıfı oluşturmak, değiştirmek veya bir hata ayıklama izleme anahtarı silin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `PAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye oluşturulan, değiştirilen veya bir hata ayıklama izlemeyi anahtar silinen yönetilen iş parçacığı içeren uygulama etki alanını temsil eder.  
  
 `pThread`  
 [in] Yönetilen iş parçacığı temsil eden bir Icordebugthread nesnesi için bir işaretçi.  
  
 `lLevel`  
 [in] Olay günlüğüne yazılan açıklayıcı ileti önem derecesi belirten bir değer.  
  
 `ulReason`  
 [in] Değerini [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) işlemi belirten numaralandırma gerçekleştirilen hata ayıklama izleme anahtarı.  
  
 `pLogSwitchName`  
 [in] Hata ayıklama izlemeyi anahtarın adı için bir işaretçi.  
  
 `pParentName`  
 [in] Hata ayıklama izleme anahtarı üst adını gösteren bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
