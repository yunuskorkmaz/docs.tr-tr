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
ms.openlocfilehash: 6c1d7db8aacaf81d47abd4a9cd972b44f56a3bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137515"
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
  
 .NET Framework sürüm 2,0 ' de, başarısız olacağı için STOP_UNMANAGED bayrağı ayarlanmış olarak `StepOut` kullanmayın. (Adımlamayı ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) kullanın.) Birlikte çalışma hata ayıklayıcıları yerel koda yönelik olarak kullanıma hazır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
