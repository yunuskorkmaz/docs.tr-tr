---
title: "ICorDebugStepper::SetInterceptMask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ef03b63c4af79c01ba9962fcc6f106b3141b576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask Yöntemi
İçine adım adım kod türlerini belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Kod türlerini belirtir Cordebugıntercept numaralandırması değerlerinin birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dinleyiciden bitini ayarlanırsa, kod kesintiye uğratan verilen türünü karşılaşıldığında Adımlayıcı tamamlayın. Bit işaretli değilse, intercepting kod atlanacak.  
  
 `SetInterceptMask` Yöntemi olabilir ile öngörülemeyen etkileşimleri [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (açısından kullanıcının). Örneğin, varsa yalnızca görünür (diğer bir deyişle, iç olmayan) sınıf başlatma kodunu kısmı eksik eşleme bilgilerini ve değil STOP_NO_MAPPING_INFO ayarlayın (bkz [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop numaralandırması için) sınıfı başlatma Adımlayıcı adım. Varsayılan olarak, yalnızca INTERCEPT_NONE değeri `CorDebugIntercept` numaralandırma kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
