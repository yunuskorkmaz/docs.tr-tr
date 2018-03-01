---
title: "ICorDebugStepper::Step Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f921725d6794f08530a537462208264ced1dc089
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step Yöntemi
Tek adım üzerinden içeren kendi iş parçacığı ve isteğe bağlı olarak, bu ICorDebugStepper neden olan tek atlama iş parçacığı denir işlevler üzerinden devam edin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bStepIn`  
 [in] Kümesine `true` iş parçacığı içinde adlı bir işlev adımla için. Kümesine `false` işlevi Adımlama için.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı bu Adımlayıcı 's çerçevede sonraki yönetilen yönerge gerçekleştirdiğinde adım tamamlar. Varsa `Step` olan Adımlayıcı üzerinde olarak adlandırılan, yönetilen kod içinde değil, sonraki yönetilen kod yönerge iş parçacığı tarafından çalıştırıldığında adımın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
