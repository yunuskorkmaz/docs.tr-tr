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
ms.openlocfilehash: 7b18474aeaa79224de5371df3ff0cac5ed9bf4ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994293"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange Yöntemi
Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı ve son belirtilen aralıkların dışında kod ulaştığında döndürülecek için neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
