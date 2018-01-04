---
title: "ICorDebugManagedCallback2::CreateConnection Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.CreateConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e0037f72e51683e5b1d62ad7ecb9aa185f53370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection Yöntemi
Hata ayıklayıcı yeni bir bağlantı oluşturulduğunu size bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Bağlantı oluşturulduğu işlemi temsil eden bir "ICorDebugProcess" nesnesi için bir işaretçi  
  
 `dwConnectionId`  
 [in] Yeni bir bağlantı kimliği.  
  
 `pConnName`  
 [in] Yeni bir bağlantı adı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 A `CreateConnection` geri çağırma harekete aşağıdaki durumlarda birini:  
  
-   Ne zaman bir hata ayıklayıcı bağlantıları içeren bir işlem ekler. Çalışma zamanı bu durumda, oluştur ve Dağıt bir `CreateConnection` olay ve [Icordebugmanagedcallback2::changeconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) işlemdeki her bağlantı için olay.  
  
-   Bir konak çağırdığında [Iclrdebugmanager::beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) içinde [barındırma API](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
