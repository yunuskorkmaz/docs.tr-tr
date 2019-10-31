---
title: ICorDebugManagedCallback2::ChangeConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 4558074bc23334bd697461a00ccb31db3e3fe397
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130606"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection Yöntemi
Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki Değiştirilen bağlantıyı içeren işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.  
  
 `dwConnectionId`  
 'ndaki Değiştirilen bağlantının KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  
 `ChangeConnection` geri çağırma aşağıdaki durumlardan biri içinde tetiklenir:  
  
- Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında. Bu durumda, çalışma zamanı işlemdeki her bağlantı için bir [ICorDebugManagedCallback2:: CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) olayı ve bir `ChangeConnection` olayı oluşturur ve gönderir. Bağlantının görev kümesinin oluşturulduktan sonra değiştirilip değiştirilmediğini bağımsız olarak, var olan her bağlantı için `ChangeConnection` bir olay oluşturulur.  
  
- Bir ana bilgisayar [barındırma API 'Sindeki](../../../../docs/framework/unmanaged-api/hosting/index.md) [ICLRDebugManager:: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) öğesini çağırdığında.  
  
 Hata ayıklayıcı, yeni değişiklikleri almak için işlemdeki tüm iş parçacıklarını taramalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
