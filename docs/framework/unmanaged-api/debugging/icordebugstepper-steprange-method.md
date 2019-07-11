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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760528"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange Yöntemi
Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı ve son belirtilen aralıkların dışında kod ulaştığında döndürülecek için neden olur.  
  
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
 [in] Kümesine `true` için iş parçacığı içinde çağrılan bir işlevin içine Adımlama. Kümesine `false` işlevi Adımlama için.  
  
 `ranges`  
 [in] Bir dizi COR_DEBUG_STEP_RANGE yapılarının her biri bir aralığını belirtir.  
  
 `cRangeCount`  
 [in] Boyutu `ranges` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `StepRange` Yöntem çalışır gibi [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) yöntemi, belirtilen aralığın dışındaki kod kadar tamamlanmazsa dışında ulaşıldı.  
  
 Bu, aynı anda tek bir yönerge Adımlama değerinden daha verimli olabilir. Aralıkları listesi Adımlayıcı 's çerçeve başından uzaklık çiftleri olarak belirtilir.  
  
 Göreli bir yöntemin Microsoft Ara dili (MSIL) kodu aralıktır. Çağrı [ICorDebugStepper::setrangeıl](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) ile `false` aralıkları yerel kod bir yöntemin göre yapma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
