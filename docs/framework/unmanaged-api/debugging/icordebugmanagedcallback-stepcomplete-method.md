---
title: ICorDebugManagedCallback::StepComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd784cb3322423e9309e8a5632822831b4e44cdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184801"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a>ICorDebugManagedCallback::StepComplete Yöntemi
Hata ayıklayıcı, bir adım tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Hangi adımın tamamlanması iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `pThread`  
 [in] Hangi adımın tamamlanması iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.  
  
 `pStepper`  
 [in] Kod yürütmeyi adımda temsil eden bir ICorDebugStepper nesne işaretçisi.  
  
 `reason`  
 [in] CorDebugStepReason sabit bir adımın sonucunu gösteren bir değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Adımlayıcı, hata ayıklama sonlandırıldı sürece Adımlama istenirse, devam etmek için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
