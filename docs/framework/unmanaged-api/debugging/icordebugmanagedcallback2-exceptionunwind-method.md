---
title: ICorDebugManagedCallback2::ExceptionUnwind Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faba9631e85ac84ff1517b64e9a3f5567ee7c9dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214801"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind Yöntemi
Özel durumu geriye doğru işlem sırasında bir durum bildirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pThread`  
 [in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.  
  
 `dwEventType`  
 [in] Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olayı belirtir CorDebugExceptionUnwindCallbackType sabit listesi değeri.  
  
 `dwFlags`  
 [in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExceptionUnwind` çeşitli noktalarda, özel durum işleme işleminin geriye doğru izleme aşamasında çağrılır. `ExceptionUnwind` birden çok kez tek bir özel durumu geriye doğru izleme çağrılabilir.  
  
 Varsa `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, yönerge işaretçisini dizisi noktadan önce iş parçacığının yaprak çerçevesinde olacaktır (önce birkaç yönergeleri olabilir) özel duruma yol açan yönerge.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
