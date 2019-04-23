---
title: ICorDebugController::SetAllThreadsDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138482"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState Yöntemi
İşlemdeki tüm yönetilen iş parçacığı hata ayıklama durumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `state`  
 [in] Hata ayıklama için iş parçacığı durumunu belirten "CorDebugThreadState" numaralandırma değeri.  
  
 `pExceptThisThread`  
 [in] Bir iş parçacığı hata ayıklama durumu ayarından muaf tutulacak temsil eden bir "ICorDebugThread" nesne işaretçisi. Bu değer null ise, hiçbir iş parçacığı muaf tutulur.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetAllThreadsDebugState` Yöntemi aracılığıyla görülemeyen iş parçacıkları etkileyebilir [EnumerateThreads yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), askıya alınan iş parçacıkları bunu `SetAllThreadsDebugState` yöntemi ile sürdürülmesini gerekecektir `SetAllThreadsDebugState` yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
