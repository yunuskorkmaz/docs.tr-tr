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
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788284"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind Yöntemi
Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `dwEventType`  
 'ndaki Geriye doğru izleme aşamasında geri çağırma tarafından bildirimekte olan olayı belirten Cordebugexceptionunwınizcallbacktype numaralandırması değeri.  
  
 `dwFlags`  
 'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExceptionUnwind`, özel durum işleme sürecinin geriye doğru izleme aşamasında çeşitli noktalarda çağrılır. tek bir özel durum geriye doğru bir şekilde `ExceptionUnwind` birden çok kez çağrılabilir.  
  
 `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED ise yönerge işaretçisi, özel duruma yol gösteren yönerge olan iş parçacığının yaprak çerçevesinde (daha önce birkaç yönerge olabilir) olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
