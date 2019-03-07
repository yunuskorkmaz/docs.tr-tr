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
ms.openlocfilehash: 25a9d287e6520f1fc7826d85dfbcd8e9a6da22f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481081"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask Yöntemi
İçine girdiğiniz kod türlerini belirten bir değeri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
