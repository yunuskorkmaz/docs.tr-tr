---
title: ICorDebug::SetManagedHandler Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 88a007654646ba42ebcaf1b42e002282a1040c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134058"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler Yöntemi
Yönetilen olaylar için olay işleyicisi nesnesini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCallback`  
 'ndaki Olay işleyicisi nesnesi olan [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetManagedHandler` oluşturma zamanında çağrılmalıdır.  
  
 `ICorDebugManagedCallback` uygulaması, hata ayıklamakta olan uygulama için hata ayıklama olaylarını işlemek üzere yeterli arabirimler içermiyorsa, `SetManagedHandler` bir HRESULT E_NOINTERFACE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
