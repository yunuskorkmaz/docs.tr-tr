---
title: ICorDebugManagedCallback::Break Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bab20301c5413f8bbe95d44b87e06d3b3870c9e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377709"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break Yöntemi

Hata ayıklayıcı bildirir, bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge kodu stream'de yürütülür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>Parametreler

`pAppDomain`\
[in] Kesme yönergesine içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.

`thread`\
[in] Bir işaretçi Icordebugthread nesneye kesme yönergesine içeren iş parçacığını temsil eder.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug.idl, CorDebug.h

**Kitaplığı:** CorGuids.lib

**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)