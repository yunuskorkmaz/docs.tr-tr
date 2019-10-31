---
title: ICorDebugManagedCallback2::DestroyConnection Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: a64df9f821021547efd08045e9f67fee25173e5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137434"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a>ICorDebugManagedCallback2::DestroyConnection Metodu
Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki Yok edilen bağlantıyı içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.  
  
 `dwConnectionId`  
 'ndaki Yok edilen bağlantının KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  
 [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md)'sinde bir ana bilgisayar [ICLRDebugManager:: EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) çağırdığında, bir `DestroyConnection` geri çağırması tetiklenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
