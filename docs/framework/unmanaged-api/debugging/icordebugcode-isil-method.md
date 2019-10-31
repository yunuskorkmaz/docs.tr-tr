---
title: ICorDebugCode::IsIL Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125558"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL Yöntemi

Bu "ICorDebugCode" değerinin Microsoft ara dil (MSIL) içinde derlenen kodu temsil edip etmediğini gösteren bir değer alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>Parametreler

`pbIL`  
[out] Bu `ICorDebugCode` MSIL 'de derlenen kodu temsil ediyorsa `true`. Aksi takdirde, `false`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
