---
title: ICorDebugStepper::Step Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493030"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step Yöntemi
Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için neden olan tek Adımlama iş parçacığının içinden çağıran işlevler ile devam edin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bStepIn`  
 [in] Kümesine `true` için iş parçacığı içinde çağrılan bir işlevin içine Adımlama. Kümesine `false` işlevi Adımlama için.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı bu adımlayıcıdaki 's çerçevede sonraki yönetilen yönergesi gerçekleştirdiğinde adımı tamamlar. Varsa `Step` olan Adımlayıcı üzerinde çağrılır, yönetilen kod içinde değil, sonraki yönetilen kod yönergesi tarafından iş parçacığı yürütüldüğünde adım tamamlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
