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
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137577"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask Yöntemi
İçine eklenen kod türlerini belirten bir değer belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mask`  
 'ndaki Kod türlerini belirten Cordebugkesmenoktası numaralandırması değerlerinin birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yakalayıcıyı için bit ayarlandıysa, verilen bir işlem kodu türü ile karşılaşıldığında Stepper tamamlanır. Bit silinirse, kesintiye uğratan kod atlanır.  
  
 `SetInterceptMask` yöntemi, [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (kullanıcının Görünüm noktasından) ile öngörülemeyen etkileşimlere sahip olabilir. Örneğin, sınıf başlatma kodunun yalnızca görünür (iç olmayan) kısmı eşleşme bilgisi ve STOP_NO_MAPPING_INFO ayarlanmamışsa (bkz. [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop Sabit Listesi), Stepper sınıf başlatma üzerinde adım adım olur. Varsayılan olarak, `CorDebugIntercept` numaralandırmanın yalnızca INTERCEPT_NONE değeri kullanılacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
