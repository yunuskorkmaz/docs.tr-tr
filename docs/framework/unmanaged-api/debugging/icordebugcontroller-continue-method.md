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
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892859"
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
'ndaki Bant dışı `true` bir olaydan devam edildiğinde olarak ayarlayın; Aksi takdirde, olarak `false`ayarlayın.

## <a name="remarks"></a>Açıklamalar

`Continue``ICorDebugController::Stop` yöntemine yapılan çağrıdan sonra işlemi devam ettirir.

Karışık modda hata ayıklama yaparken, bir bant dışı olaydan `Continue` devam etmediğiniz takdirde Win32 olay iş parçacığı üzerinde çağırmayın.

*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı `fOutOfBand` `false` [ICorDebugUnmanagedCallback: parametresi olarak ayarlanmış:D ebugevent geri aramasını](icordebugunmanagedcallback-debugevent-method.md) alır.

*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` parametresi olarak ayarlanmış şekilde `true`geri çağırma işlemini alır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
