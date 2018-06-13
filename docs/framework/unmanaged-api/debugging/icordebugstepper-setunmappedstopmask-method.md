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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419916"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask Yöntemi
İçinde yürütme durdurulur eşlenmemiş kod türünü belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Hata ayıklayıcı yürütme durdurulur eşlenmemiş kod türünü belirtir CorDebugUnmappedStop numaralandırması değeri.  
  
 STOP_OTHER_UNMAPPED varsayılan değerdir. STOP_UNMANAGED değeri yalnızca birlikte çalışma hata ayıklamaya geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcıyı Microsoft Ara dile (MSIL) karşılık gelen hiçbir eşleme sahip bir tam zamanında (JIT) derleme bulduğunda, bu tür bir eşlenmemiş kod belirtme bayrağı ayarlarsanız yürütme durdurur; Aksi takdirde, saydam atlama devam eder.  
  
 Hata ayıklayıcı, bir yöntem girmek için Adımlayıcı kullanmıyorsa, sonra da mutlaka eşlenmemiş kod adım olmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
