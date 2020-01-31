---
title: ICorDebugStepper::StepOut Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 08cf2d0bb09080296fc1fcc69b5817f4d6118765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791723"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut Yöntemi
Bu ICorDebugStepper, kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `StepOut` işlem, normal olarak geçerli çerçeveden çağırma çerçevesine döndürülmeden sonra tamamlanır.  
  
 Yönetilmeyen kod içinde `StepOut` çağrılırsa, geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde adım tamamlanır.  
  
 .NET Framework sürüm 2,0 ' de, başarısız olacağı için STOP_UNMANAGED bayrağıyla ayarlanmış `StepOut` kullanmayın. (Adımlamayı ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) kullanın.) Birlikte çalışma hata ayıklayıcıları yerel koda yönelik olarak kullanıma hazır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
