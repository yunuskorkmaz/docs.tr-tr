---
description: 'Daha fazla bilgi edinin: ICorDebugManagedCallback2:: CreateConnection Yöntemi'
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
ms.openlocfilehash: c7ac91217d43531505dc27a20da9cf4534366119
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790912"
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

 `CreateConnection`Aşağıdaki durumlardan birinde bir geri çağırma harekete geçirilir:  
  
- Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında. Bu durumda, çalışma zamanı `CreateConnection` işlemdeki her bağlantı için bir olay ve bir [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) olayı oluşturur ve gönderir.  
  
- Bir ana bilgisayar [BARıNDıRMA API](../hosting/index.md)'Sinde [ICLRDebugManager:: BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) öğesini çağırdığında.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
