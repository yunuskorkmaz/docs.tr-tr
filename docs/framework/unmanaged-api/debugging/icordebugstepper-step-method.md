---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper:: Step yöntemi'
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
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717634"
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
 'ndaki `true` İş parçacığı içinde çağrılan bir işleve adım adım olarak ayarlanır. `false`İşlevin üzerinde adımla için olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanı, bu Stepper 'in çerçevesinde bir sonraki yönetilen yönergeyi gerçekleştirdiğinde adım tamamlanır. `Step`Yönetilen kodda olmayan bir Stepper üzerinde çağrılırsa, sonraki yönetilen kod yönergesi iş parçacığı tarafından yürütüldüğünde adım tamamlanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
