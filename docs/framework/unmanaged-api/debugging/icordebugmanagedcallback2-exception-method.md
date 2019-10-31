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
ms.openlocfilehash: f40030a2034057e83de51a21655a686f30b9ee88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137449"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception Yöntemi
Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Özel durumun oluşturulduğu iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `pFrame`  
 'ndaki `dwEventType` parametresi tarafından belirlendiği şekilde, bir çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi. Daha fazla bilgi için, açıklamalar bölümündeki tabloya bakın.  
  
 `nOffset`  
 'ndaki `dwEventType` parametresi tarafından belirlendiği şekilde, bir sapmayı belirten tamsayı. Daha fazla bilgi için, açıklamalar bölümündeki tabloya bakın.  
  
 `dwEventType`  
 'ndaki Bu özel durum geri çağrısının türünü belirten CorDebugExceptionCallbackType numaralandırması değeri.  
  
 `dwFlags`  
 'ndaki Özel durum hakkında ek bilgi belirten [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) sabit listesinin bir değeri  
  
## <a name="remarks"></a>Açıklamalar  
 `Exception` geri çağırması, özel durum işleme işleminin arama aşamasında çeşitli noktalarda çağrılır. Diğer bir deyişle, özel durum geriye doğru bir şekilde bir kez çağrılabilir.  
  
 İşlenmekte olan özel durum, `pThread` parametresi tarafından başvurulan ICorDebugThread nesnesinden alınabilir.  
  
 Belirli bir çerçeve ve fark, `dwEventType` parametresine göre belirlenir:  
  
|`dwEventType` değeri|`pFrame` değeri|`nOffset` değeri|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Özel durumu oluşturan çerçeve.|Çerçevedeki yönerge işaretçisi.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Oluşturulan özel durum noktasına en yakın Kullanıcı kodu çerçevesi.|Çerçevedeki yönerge işaretçisi.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Catch işleyicisini içeren çerçeve.|Catch işleyicisinin başlangıcının Microsoft ara dili (MSIL) kayması.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Tanımlayan.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
