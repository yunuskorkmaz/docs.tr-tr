---
title: ICorDebugManagedCallback::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4e7b62b7eb038d553b28fbd6422175d511df88d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540552"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess Yöntemi
Hata ayıklayıcı bir işlemden çıkıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProcess`  
 [in] Bir işlemi temsil eden bir Icordebugprocess nesne işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Devam edemiyor bir `ExitProcess` olay. İşlem durdurulacak görüntülenirken bu olay için diğer olayları zaman uyumsuz olarak harekete. Bu işlem genellikle nedeniyle bazı dış zorla durdurulduğu sırada sona ererse ortaya çıkabilir.  
  
 Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri gönderme, geri arama tarafından döndürülen sonra bu olay kadar geciktirilecek.  
  
 `ExitProcess` Kapanışında çağrılmadığı kesin yalnızca çıkış/yüklemeyi kaldırma olay etkinliğidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
