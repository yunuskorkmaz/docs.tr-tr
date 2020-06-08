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
ms.openlocfilehash: 7d209b7c319baff912b3462f8ed5f3f30f127750
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501917"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection Yöntemi
Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 `ChangeConnection`Aşağıdaki durumlardan birinde bir geri çağırma harekete geçirilir:  
  
- Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında. Bu durumda, çalışma zamanı bir [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) olayı ve `ChangeConnection` işlemdeki her bağlantı için bir olay oluşturur ve gönderir. `ChangeConnection`Bağlantının görev kümesinin oluşturulduktan sonra değiştirilip değiştirilmediğini bağımsız olarak, var olan her bağlantı için bir olay oluşturulur.  
  
- Bir ana bilgisayar [barındırma API 'Sindeki](../hosting/index.md) [ICLRDebugManager:: SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) öğesini çağırdığında.  
  
 Hata ayıklayıcı, yeni değişiklikleri almak için işlemdeki tüm iş parçacıklarını taramalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
