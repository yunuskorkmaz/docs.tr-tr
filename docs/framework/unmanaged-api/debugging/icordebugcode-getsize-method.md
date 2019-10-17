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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25349f7c8274b818df2cd1bc5d67856e31efecc4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395540"
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
dışı Bu `ICorDebugCode` nesnesinin temsil ettiği ikili kodun bayt cinsinden boyutu için bir işaretçi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
