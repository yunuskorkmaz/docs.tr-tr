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
ms.openlocfilehash: 97a4a464d3dfb7b333f44ac4206bd880fd171e16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723421"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler Yöntemi

Yönetilen olaylar için olay işleyicisi nesnesini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pCallback`  
 'ndaki Olay işleyicisi nesnesi olan [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetManagedHandler` Oluşturulma zamanında çağrılmalıdır.  
  
 Uygulama, `ICorDebugManagedCallback` hataları ayıklanan uygulamanın hata ayıklama olaylarını işlemek için yeterli arabirimler içermiyorsa, `SetManagedHandler` E_NOINTERFACE hresult döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
