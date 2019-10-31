---
title: ICorDebugStepper::SetRangeIL Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137537"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL Yöntemi
[ICorDebugStepper:: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göre veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) koduna göreli bağımsız değişken değerlerini geçirip geçirmeyeceğini belirten bir değer belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIL`  
 'ndaki Aralıkların MSIL koduna göreli olduğunu belirtmek için `true` olarak ayarlayın. Aralıkların yerel koda göreli olduğunu belirtmek için `false` olarak ayarlayın. Varsayılan değer `true` şeklindedir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
