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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137527"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step Yöntemi
Bu ICorDebugStepper, kendi iş parçacığı içinde tek adımlı ve isteğe bağlı olarak, iş parçacığı içinde çağrılan işlevler aracılığıyla tek adımla devam etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bStepIn`  
 'ndaki İş parçacığı içinde çağrılan bir işleve adımla `true` olarak ayarlayın. İşlevin üzerinde adımla `false` olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı, bu Stepper 'in çerçevesinde bir sonraki yönetilen yönergeyi gerçekleştirdiğinde adım tamamlanır. `Step` yönetilen kodda olmayan bir Stepper üzerinde çağrılırsa, sonraki yönetilen kod yönergesi iş parçacığı tarafından yürütüldüğünde adım tamamlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
