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
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760562"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut Yöntemi
Tek adımlı içeren kendi iş parçacığı ve geçerli çerçeve arama çerçeveye denetim döndürdüğünde tamamlanması için bu ICorDebugStepper neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
