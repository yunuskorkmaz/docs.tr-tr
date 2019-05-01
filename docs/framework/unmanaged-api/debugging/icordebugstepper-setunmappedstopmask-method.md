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
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987460"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask Yöntemi
Yürütmeyi durdur eşlenmemiş kodun türünü belirten bir değeri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Hata ayıklayıcı yürütme durdurulur eşlenmemiş kodun türünü belirten CorDebugUnmappedStop sabit listesi değeri.  
  
 STOP_OTHER_UNMAPPED varsayılan değerdir. ' % S'değeri STOP_UNMANAGED yalnızca birlikte çalışma hata ayıklama ile geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Microsoft Ara dilini (MSIL) için karşılık gelen bir eşlemesi olmayan bir tam zamanında (JIT) derleme bulduğunda eşlenmemiş kod türünü belirten bayrağı ayarlarsanız yürütmeyi durdurur; Aksi takdirde, Adımlama şeffaf bir şekilde devam eder.  
  
 Hata ayıklayıcı, bir yönteme girmeyi Adımlayıcı kullanmıyorsa, sonra da mutlaka eşlenmemiş bir kod üzerinde Adım olmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
