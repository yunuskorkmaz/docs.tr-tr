---
title: ICorDebugStepper2::SetJMC Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379468"
---
# <a name="icordebugstepper2setjmc-method"></a>ICorDebugStepper2::SetJMC Yöntemi
Bu ICorDebugStepper adımlarının yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla ilgili olduğunu belirten bir değer ayarlar. Bu işlem yalnızca kendi kodum (JMC) hata ayıklaması olarak da bilinir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fIsJMCStepper`  
 'ndaki `true`Yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla adım adım olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
