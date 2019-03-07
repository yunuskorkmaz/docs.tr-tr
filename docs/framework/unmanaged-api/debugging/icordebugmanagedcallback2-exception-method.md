---
title: ICorDebugManagedCallback2::Exception Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f776f20f163df91d65509e5dbab31fe9c29a965
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492107"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception Yöntemi
Hata ayıklayıcı özel durum işleyicisi için arama başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Özel durumun oluştuğu iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pThread`  
 [in] Özel durumun oluştuğu iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.  
  
 `pFrame`  
 [in] Bir çerçeve tarafından belirlenen şekilde temsil eden bir Icordebugframe nesne işaretçisi `dwEventType` parametresi. Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.  
  
 `nOffset`  
 [in] Tarafından belirlenen şekilde bir uzaklık belirten bir tamsayı `dwEventType` parametresi. Daha fazla bilgi için Açıklamalar bölümü içindeki tabloya bakın.  
  
 `dwEventType`  
 [in] Bu özel durum geri arama türünü belirten CorDebugExceptionCallbackType sabit listesi değeri.  
  
 `dwFlags`  
 [in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ek bilgi belirten sabit listesi  
  
## <a name="remarks"></a>Açıklamalar  
 `Exception` Geri çağırma çeşitli noktalarda özel durum işleme işleminin arama aşamasında çağrılır. Diğer bir deyişle, çağrılabilir birden çok kez bir özel durumu geriye doğru izleme çalışırken.  
  
 İşlenmekte olan özel durum tarafından başvurulan Icordebugthread nesnesinden alınabilir `pThread` parametresi.  
  
 Uzaklık ve belirli çerçeve tarafından belirlenen `dwEventType` parametresini aşağıdaki şekilde:  
  
|Değeri `dwEventType`|Değeri `pFrame`|Değeri `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Özel durum oluşturdu çerçeve.|Çerçevede yönerge işaretçisi.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Oluşturulan özel durumun noktaya en yakın kullanıcı kodu çerçevesi.|Çerçevede yönerge işaretçisi.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Catch işleyicisi içeren çerçeve.|Catch işleyicisi başına Microsoft Ara dili (MSIL) uzaklığı.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Tanımlı değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
