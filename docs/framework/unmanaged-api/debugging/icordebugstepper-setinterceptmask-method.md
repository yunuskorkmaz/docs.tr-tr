---
title: ICorDebugStepper::SetInterceptMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b644227a6085352bed682f0ddd7c3455b54895
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760695"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask Yöntemi
İçine girdiğiniz kod türlerini belirten bir değeri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Kod türlerini belirtir Cordebugıntercept sabit listesi değerlerinin birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dinleyiciyi bitini ayarlarsanız, verilen kod kesintiye türünü karşılaşıldığında Adımlayıcı tamamlayın. Araya giren kodu bit işaretli değilse, atlanacak.  
  
 `SetInterceptMask` Yöntemi olabilir öngörülemeyen etkileşim [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (açısından kullanıcının). Örneğin, yalnızca görünür (diğer bir deyişle, iç olmayan) sınıf başlatma kodu kısmı eksik eşleme bilgilerini ve STOP_NO_MAPPING_INFO ayarlanmamış (bkz [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop numaralandırması için) sınıf başlatma Adımlayıcı adım adım anlatır. Varsayılan olarak, yalnızca INTERCEPT_NONE değerini `CorDebugIntercept` sabit listesi kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
