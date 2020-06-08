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
ms.openlocfilehash: a3093f33f2220b22b7b4b373f6d79a341abf8c9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501943"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a>ICorDebugManagedCallback2::DestroyConnection Metodu
Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 `DestroyConnection` [Barındırma API](../hosting/index.md)'sinde bir ana bilgisayar [ICLRDebugManager:: EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) çağırdığında bir geri çağırma tetiklenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
