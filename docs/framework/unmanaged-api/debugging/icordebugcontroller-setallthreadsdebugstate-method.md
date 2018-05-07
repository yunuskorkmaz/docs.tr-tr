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
ms.openlocfilehash: 8ee396c512dca2bea0a7a9737d5515defce4b2b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState Yöntemi
Tüm yönetilen iş parçacığı hata ayıklama durumunu işleminde ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `state`  
 [in] Hata ayıklama için iş parçacığı durumunu belirtir "CorDebugThreadState" numaralandırma değeri.  
  
 `pExceptThisThread`  
 [in] Hata ayıklama durumu ayarından muaf için bir iş parçacığı temsil eden bir "ICorDebugThread" nesnesi için bir işaretçi. Bu değer null ise, hiçbir iş parçacığı bırakılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetAllThreadsDebugState` Yöntemi aracılığıyla görünür olmayan iş parçacıklarının etkileyebilir [EnumerateThreads yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), ile askıya alınan bunu iş parçacığı `SetAllThreadsDebugState` yöntemi ile devam ettirilebilir gerekecektir `SetAllThreadsDebugState` yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
