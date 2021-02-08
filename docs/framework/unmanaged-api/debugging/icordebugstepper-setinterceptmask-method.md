---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper:: Setyakatmask yöntemi'
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
ms.openlocfilehash: 33a42b154d063a29022034fd8061599a5e0e5503
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803554"
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
  
 `SetInterceptMask`Yöntem, [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (kullanıcının Görünüm noktasından) ile öngörülemeyen etkileşimlere sahip olabilir. Örneğin, sınıf başlatma kodunun yalnızca görünür (diğer bir deyişle, iç olmayan) kısmı, bilgi ve STOP_NO_MAPPING_INFO ayarlanmamışsa (bkz. [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) yöntemi ve CorDebugUnmappedStop sabit listesi), Stepper sınıfı başlatma üzerinde adım adım olur. Varsayılan olarak, numaralandırmanın yalnızca INTERCEPT_NONE değeri `CorDebugIntercept` kullanılacaktır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
