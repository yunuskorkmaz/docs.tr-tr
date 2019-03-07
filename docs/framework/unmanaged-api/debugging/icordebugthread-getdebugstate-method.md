---
title: ICorDebugThread::GetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68df19120f2e0b45e73f9d5e137afc8a5e7ac513
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489897"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState Yöntemi
Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pState`  
 [out] Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan karşılaştırmaya CorDebugThreadState sabit listesi değerleri için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu varsa, bu iş parçacığı için var olan hata ayıklama durumunu temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
