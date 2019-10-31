---
title: ICorDebugManagedCallback2::CreateConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: d83ad530c8a61c2bfc38fb46ad2a33ef8d5077d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130583"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection Yöntemi
Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki Bağlantının oluşturulduğu işlemi temsil eden bir "ICorDebugProcess" nesnesi işaretçisi  
  
 `dwConnectionId`  
 'ndaki Yeni bağlantının KIMLIĞI.  
  
 `pConnName`  
 'ndaki Yeni bağlantının adı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateConnection` geri çağırma aşağıdaki durumlardan biri içinde tetiklenir:  
  
- Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında. Bu durumda, çalışma zamanı, işlemdeki her bağlantı için bir `CreateConnection` olayı ve bir [ICorDebugManagedCallback2:: ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) olayı oluşturur ve gönderir.  
  
- Bir ana bilgisayar [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md)'Sinde [ICLRDebugManager:: BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) öğesini çağırdığında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
