---
title: ICorDebugCode::GetSize Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
ms.openlocfilehash: 2370ff5d99078ceb1ae0509e660c046dd7a1537e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125614"
---
# <a name="icordebugcodegetsize-method"></a>ICorDebugCode::GetSize Metodu

Bu "ICorDebugCode" ile temsil edilen ikili kodun boyutunu bayt cinsinden alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a>Parametreler

`pcBytes`  
dışı Bu `ICorDebugCode` nesnenin temsil ettiği ikili kodun bayt cinsinden boyutu için bir işaretçi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
