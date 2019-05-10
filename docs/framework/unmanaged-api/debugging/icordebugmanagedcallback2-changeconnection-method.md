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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06246434097ede2896d7f1b496348fe5d575744
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624520"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection Yöntemi
Hata ayıklayıcı, belirtilen bağlantı ile ilişkili görevlerin değiştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Değiştirilen bağlantıyı içeren işlemini temsil eden bir "ICorDebugProcess" nesneye bir işaretçi.  
  
 `dwConnectionId`  
 [in] Değiştirilen bağlantının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 A `ChangeConnection` geri çağırma harekete aşağıdaki durumlarda birini:  
  
- Ne zaman bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirir. Çalışma zamanı bu durumda, oluşturma ve gönderme bir [Icordebugmanagedcallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) olay ve `ChangeConnection` işlemdeki her bağlantı için olay. A `ChangeConnection` olay görevleri bu bağlantının kümesi oluşturulduktan sonra değiştirilmiş olan bağımsız olarak mevcut her bağlantı için oluşturulur.  
  
- Bir konak çağırdığında [Iclrdebugmanager::setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) içinde [barındırma API](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Hata ayıklayıcı, yeni değişikliklerini işlemdeki tüm iş parçacıkları taramalısınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
