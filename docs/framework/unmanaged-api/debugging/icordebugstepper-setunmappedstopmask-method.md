---
title: ICorDebugStepper::SetUnmappedStopMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137558"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask Yöntemi
Yürütmenin durdurmayacak eşlenmemiş kodun türünü belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mask`  
 'ndaki Hata ayıklayıcının yürütmeyi durdurulacağı eşlenmemiş kodun türünü belirten CorDebugUnmappedStop numaralandırması değeri.  
  
 Varsayılan değer STOP_OTHER_UNMAPPED ' dir. STOP_UNMANAGED değeri yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı, Microsoft ara dili (MSIL) için karşılık gelen hiçbir eşleme olmayan bir tam zamanında (JıT) derleme bulduğunda, bu tür eşlenmemiş kod belirten bayrak ayarlandıysa yürütmeyi halliyorlar. Aksi halde, bu adım saydam olarak devam eder.  
  
 Hata ayıklayıcı bir yöntemi girmek için bir Stepper kullanmıyorsa, eşlenmemiş kod üzerinde adım adım değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
