---
title: ICorDebugManagedCallback::ControlCTrap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: da35db8a943fda5fb3fbf4126684bb9cb7243001
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137421"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>ICorDebugManagedCallback::ControlCTrap Yöntemi
Hata ayıklayıcıya CTRL + C 'nin hata ayıklamakta olan işlemde yakalandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki CTRL + C 'nin bindirildiği işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Hata ayıklayıcı CTRL + C yakalamasını işleymeyecektir.|  
|S_FALSE|Hata ayıklayıcı CTRL + C yakalamasını işlemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemdeki tüm uygulama etki alanları bu geri çağırma için durdurulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
