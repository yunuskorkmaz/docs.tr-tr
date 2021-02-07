---
description: 'Daha fazla bilgi edinin: ICorDebugStepper:: StepRange yöntemi'
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
ms.openlocfilehash: 868925ef301cca15b7887505e879f5fff02002e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717595"
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
 'ndaki `true` İş parçacığı içinde çağrılan bir işleve adım adım olarak ayarlanır. `false`İşlevin üzerinde adımla için olarak ayarlayın.  
  
 `ranges`  
 'ndaki Her biri bir Aralık belirten COR_DEBUG_STEP_RANGE yapılarından oluşan dizi.  
  
 `cRangeCount`  
 'ndaki `ranges` Dizinin boyutu.  
  
## <a name="remarks"></a>Açıklamalar  

 `StepRange`Yöntemi, [ICorDebugStepper:: Step](icordebugstepper-step-method.md) yöntemi gibi çalışarak, belirtilen aralığın dışındaki koda ulaşılana kadar tamamlanmaz.  
  
 Tek seferde bir yönergeyi adımlamayı kullanmaktan daha etkili olabilir. Aralıklar, Stepper 'ın çerçevesinin başından itibaren bir konum çiftleri listesi olarak belirtilir.  
  
 Aralıklar bir yöntemin Microsoft ara dili (MSIL) koduna göredir. [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) öğesini, `false` aralıkları bir yöntemin yerel koduna göre yapmak için ile çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
