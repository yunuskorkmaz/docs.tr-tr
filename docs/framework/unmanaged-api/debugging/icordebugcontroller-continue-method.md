---
title: ICorDebugController::Continue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e2be44165472e2fbf368f61b865d39a5e9fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395459"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue Yöntemi

[Durdurma yöntemine](icordebugcontroller-stop-method.md)yapılan çağrıdan sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>Parametreler

`fIsOutOfBand`  
'ndaki Bant dışı bir olaydan devam ederseniz, `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın.

## <a name="remarks"></a>Açıklamalar

`Continue` `ICorDebugController::Stop` yöntemine yapılan çağrıdan sonra işlem devam ettirir.

Karışık modda hata ayıklama yaparken, bir bant dışı olaydan devam etmediğiniz takdirde Win32 olay iş parçacığında `Continue` ' ı çağırmayın.

*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı [ICorDebugUnmanagedCallback::D ebugEvent](icordebugunmanagedcallback-debugevent-method.md) geri aramasını alır `fOutOfBand` parametresi `false` olarak ayarlanmıştır.

*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı `fOutOfBand` parametresiyle `true` olarak ayarlanan `ICorDebugUnmanagedCallback::DebugEvent` geri aramasını alır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
