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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9b4ee64022374cb4e1950acceb3f32925b736bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994298"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL Yöntemi
Belirten bir değeri ayarlar olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) göreli yerel kod veya Microsoft göreli olan değerleri Ara dil (MSIL) kodu basamaklı yöntemin bağımsız değişken geçirin aracılığıyla.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIL`  
 [in] Kümesine `true` aralıkları MSIL kodu göreli olduğunu belirtmek için. Kümesine `false` aralıkları yerel kod göreli olduğunu belirtmek için. Varsayılan değer `true` şeklindedir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
