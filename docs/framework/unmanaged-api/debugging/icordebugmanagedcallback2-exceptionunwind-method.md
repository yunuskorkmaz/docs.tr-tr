---
title: "ICorDebugManagedCallback2::ExceptionUnwind Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64b85311f625e39dd25c48a60dde2fbaf66a957f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind Yöntemi
Özel durum unwinding işlemi sırasında bir durum bildirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye özel durum oluştu iş parçacığı içeren uygulama etki alanını temsil eder.  
  
 `pThread`  
 [in] Bir işaretçi Icordebugthread nesneye özel durum oluştu iş parçacığı temsil eder.  
  
 `dwEventType`  
 [in] Geri çağırma göre geriye doğru izleme aşamasında işaret olayı belirtir CorDebugExceptionUnwindCallbackType numaralandırması değeri.  
  
 `dwFlags`  
 [in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ayrıntılı bilgileri belirtir numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExceptionUnwind`çeşitli noktalarda, özel durum işleme işleminin bırakma aşamasında çağrılır. `ExceptionUnwind`birden çok kez tek bir özel durum geriye doğru izleme sırasında çağrılabilir.  
  
 Varsa `dwEventType` DEBUG_EXCEPTION_INTERCEPTED, = yönerge işaretçisi önce dizisi noktada iş parçacığının yaprak çerçevesinde olacaktır (önce birkaç yönergeleri olabilir) özel durumu öncülük yönerge.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
