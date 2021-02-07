---
description: ': ICorDebugController:: Continue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710809"
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
'ndaki `true` Bant dışı bir olaydan devam edildiğinde olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .

## <a name="remarks"></a>Açıklamalar

`Continue` yöntemine yapılan çağrıdan sonra işlemi devam ettirir `ICorDebugController::Stop` .

Karışık modda hata ayıklama yaparken, `Continue` bir bant dışı olaydan devam etmediğiniz takdirde Win32 olay iş parçacığı üzerinde çağırmayın.

*Bant içi olay* , hata ayıklayıcının işlemin yönetilen durumuyla etkileşimi desteklediği yönetilen bir olaydır veya normal yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı [ICorDebugUnmanagedCallback: parametresi olarak ayarlanmış:D ebugEvent geri aramasını](icordebugunmanagedcallback-debugevent-method.md) alır `fOutOfBand` `false` .

*Bant dışı bir olay* , işlem olay nedeniyle durdurulduğunda işlemin yönetilen durumuyla etkileşimi mümkün olmadığı sürece yönetilmeyen bir olaydır. Bu durumda, hata ayıklayıcı `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` parametresi olarak ayarlanmış şekilde geri çağırma işlemini alır `true` .

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
