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
ms.openlocfilehash: faefff879142d66c4c596f1b30a25e349a4014b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421807"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception Yöntemi
Hata ayıklayıcı bir özel durum işleyici için bir arama başlatıldı bildirir.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye özel durum oluştu iş parçacığı içeren uygulama etki alanını temsil eder.  
  
 `pThread`  
 [in] Bir işaretçi Icordebugthread nesneye özel durum oluştu iş parçacığı temsil eder.  
  
 `pFrame`  
 [in] Tarafından belirlenen şekilde bir çerçeve temsil eden bir Icordebugframe nesnesi için bir işaretçi `dwEventType` parametresi. Daha fazla bilgi için açıklamalar bölümündeki tabloya bakın.  
  
 `nOffset`  
 [in] Tarafından belirlenen şekilde bir uzaklık belirten bir tamsayı `dwEventType` parametresi. Daha fazla bilgi için açıklamalar bölümündeki tabloya bakın.  
  
 `dwEventType`  
 [in] Bu özel durum geri çağırma türünü belirtir CorDebugExceptionCallbackType numaralandırması değeri.  
  
 `dwFlags`  
 [in] Değerini [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) özel durum hakkında ayrıntılı bilgileri belirtir numaralandırması  
  
## <a name="remarks"></a>Açıklamalar  
 `Exception` Geri çağırma çeşitli noktalarda, özel durum işleme işleminin arama aşamasında çağrılır. Diğer bir deyişle, onu çağrılabilir birden çok kez bir özel durum geriye doğru izleme açıkken.  
  
 İşlenmekte olan özel durum tarafından başvurulan Icordebugthread nesnesinden alınabilir `pThread` parametresi.  
  
 Uzaklık ve belirli çerçevesi tarafından belirlenen `dwEventType` şekilde parametre:  
  
|Değeri `dwEventType`|Değeri `pFrame`|Değeri `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Özel durum oluşturdu çerçevesi.|Yönerge işaretçisi çerçevesinde.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Kullanıcı kodu çerçeve oluşturulan özel durum noktasına yakın.|Yönerge işaretçisi çerçevesinde.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Catch işleyicisini içeren çerçeve.|Catch işleyicisi başlangıcını Microsoft Ara dili (MSIL) uzaklığı.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Tanımlanmamış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
