---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugStepper:: StepOut yöntemi'
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
ms.openlocfilehash: ef404c928ab711aef8032655a02cbd917416e806
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717621"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut Yöntemi

Bu ICorDebugStepper, kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `StepOut`İşlem, normal olarak geçerli çerçeveden çağırma çerçevesine döndürülmeden sonra tamamlanır.  
  
 `StepOut`Yönetilmeyen kod içinde çağrılırsa, geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde adım tamamlanır.  
  
 .NET Framework sürüm 2,0 ' de, `StepOut` başarısız olacağı için STOP_UNMANAGED bayrağıyla birlikte kullanmayın. (Adımlamayı ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) kullanın.) Birlikte çalışma hata ayıklayıcıları yerel koda yönelik olarak kullanıma hazır olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
