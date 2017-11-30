---
title: "ICorDebugManagedCallback::ExitProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff80462c722a84ef68ac8c6703ded3e7138a1939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess Yöntemi
Hata ayıklayıcı işlem yaptı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Bir işaretçi Icordebugprocess nesneye işlemi temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Devam edilemiyor bir `ExitProcess` olay. İşlemi durdurulacak görüntülenirken bu olay için diğer olaylar zaman uyumsuz olarak tetikleyin. Bu durum genellikle bazı dış zorla nedeniyle durduruldu sırada işlemi sonlandırır ortaya çıkabilir.  
  
 Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor, bu geri döndü sonra bu olay kadar geciktirilir.  
  
 `ExitProcess` Kapanışında çağrılmadığı garanti yalnızca çıkış/unload olayı bir olaydır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugmanagedcallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
