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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987434"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut Yöntemi
Tek adımlı içeren kendi iş parçacığı ve geçerli çerçeve arama çerçeveye denetim döndürdüğünde tamamlanması için bu ICorDebugStepper neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 A `StepOut` normalde çağıran çerçeveyi geçerli çerçevesinden döndüğünüzde işlemi tamamlanır.  
  
 Varsa `StepOut` aldığında çağrılan geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde, yönetimsiz kod içinde adım tamamlanır.  
  
 .NET Framework sürüm 2. 0'da, kullanmayın `StepOut` ile STOP_UNMANAGED bayrağı ayarlanmış olduğundan işlem başarısız olur. (Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlama için bayrakları ayarlamanızı.) Birlikte çalışma hata ayıklayıcıları için yerel kod kendilerini gerekir dışarı adımla.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
