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
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760573"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step Yöntemi
Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı aracılığıyla ve isteğe bağlı olarak için için neden olan tek Adımlama iş parçacığının içinden çağıran işlevler ile devam edin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
