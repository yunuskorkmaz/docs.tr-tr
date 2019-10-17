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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7cbadbd1494d5e4d1488dd12296f4f90890127
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395492"
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
[out] `true` bu `ICorDebugCode`, MSIL içinde derlenen kodu temsil ediyorsa; Aksi takdirde, `false`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
