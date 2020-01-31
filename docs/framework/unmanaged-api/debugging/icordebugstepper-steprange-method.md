---
title: ICorDebugStepper::StepRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791715"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange Yöntemi
Bu ICorDebugStepper, kendi kapsayıcı iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında geri dönüşmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bStepIn`  
 'ndaki İş parçacığı içinde çağrılan bir işleve adımla `true` olarak ayarlayın. İşlevin üzerinde adımla `false` olarak ayarlayın.  
  
 `ranges`  
 'ndaki Her biri bir Aralık belirten COR_DEBUG_STEP_RANGE yapılarından oluşan dizi.  
  
 `cRangeCount`  
 'ndaki `ranges` dizisinin boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 `StepRange` yöntemi [ICorDebugStepper:: Step](icordebugstepper-step-method.md) yöntemi gibi çalışarak, belirtilen aralığın dışındaki koda ulaşılana kadar tamamlanmaz.  
  
 Tek seferde bir yönergeyi adımlamayı kullanmaktan daha etkili olabilir. Aralıklar, Stepper 'ın çerçevesinin başından itibaren bir konum çiftleri listesi olarak belirtilir.  
  
 Aralıklar bir yöntemin Microsoft ara dili (MSIL) koduna göredir. Aralıkları bir yöntemin yerel koduyla ilişkili hale getirmek için `false` ile [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
