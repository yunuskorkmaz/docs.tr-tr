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
ms.openlocfilehash: e98748b523b948dc002f2ebc4e2e79fc7d659918
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781589"
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
  
- Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında. Bu durumda, çalışma zamanı, işlemdeki her bağlantı için bir `CreateConnection` olayı ve bir [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) olayı oluşturur ve gönderir.  
  
- Bir ana bilgisayar [BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md)'Sinde [ICLRDebugManager:: BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) öğesini çağırdığında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
