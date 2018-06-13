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
ms.openlocfilehash: 68288111e3f862cf1364031eaad9c63cf347146f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415944"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection Yöntemi
Hata ayıklayıcı belirtilen bağlantı ile ilişkili görevlerin değiştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Değiştirilen bağlantıyı içeren işlemi temsil eden bir "ICorDebugProcess" nesnesi için bir işaretçi.  
  
 `dwConnectionId`  
 [in] Değiştirilen bağlantının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 A `ChangeConnection` geri çağırma harekete aşağıdaki durumlarda birini:  
  
-   Ne zaman bir hata ayıklayıcı bağlantıları içeren bir işlem ekler. Çalışma zamanı bu durumda, oluştur ve Dağıt bir [Icordebugmanagedcallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) olay ve `ChangeConnection` işlemdeki her bağlantı için olay. A `ChangeConnection` olay görevler bu bağlantının kümesi oluşturulduktan sonra değiştirildi bağımsız olarak her var olan bağlantısı için oluşturulur.  
  
-   Bir konak çağırdığında [Iclrdebugmanager::setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) içinde [barındırma API](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Hata ayıklayıcı yeni değişiklikleri almak için işlemdeki tüm iş parçacıklarını taramalısınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
