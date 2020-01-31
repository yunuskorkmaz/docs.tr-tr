---
title: ICorDebugStepper::IsActive Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791782"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive Yöntemi
Bu ICorDebugStepper Şu anda bir adım yürütüp yürütmediğini gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbActive`  
 dışı Stepper Şu anda bir adım yürütülerek `true` döndürür; Aksi takdirde, `false`döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı bir [ICorDebugManagedCallback:: Steptamamlanma](icordebugmanagedcallback-stepcomplete-method.md) çağrısını alıncaya kadar herhangi bir adım eylemi etkin kalır. Bu, Stepper otomatik olarak devre dışı bırakır. Bir Stepper, geri çağırma koşuluna ulaşılmadan önce [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) çağırarak zamanından önce devre dışı bırakılmış olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
