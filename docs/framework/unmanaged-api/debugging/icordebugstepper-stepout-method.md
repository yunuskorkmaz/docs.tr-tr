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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut Yöntemi
Tek adımlı içeren kendi iş parçacığı üzerinden ve geçerli çerçeve denetim arama çerçevenin geri döndüğünde tamamlamak için bu ICorDebugStepper neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 A `StepOut` işlemi, geçerli çerçevesinden normalde arama çerçeveye döndüğünüzde tamamlanır.  
  
 Varsa `StepOut` aldığında çağrılan adlı Yönetilen kod için geçerli çerçevenin geri döndüğünde yönetilmeyen kodunda adım tamamlayacak.  
  
 .NET Framework sürüm 2. 0'da, kullanmayın `StepOut` ile STOP_UNMANAGED bayrağı ayarlanmış çünkü başarısız. (Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) atlama bayrakları ayarlamak için.) Birlikte çalışma hata ayıklayıcıları yerel koda kendilerini olmalıdır dışarı adım.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
