---
title: ICorDebugCodeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125519"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next Yöntemi

Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugCode" örneklerinin sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>Parametreler

`celt`  
'ndaki Alınacak `ICorDebugCode` örneklerinin sayısı.

`values`  
dışı Her biri bir `ICorDebugCode` nesnesine işaret eden işaretçiler dizisi.

`pceltFetched`  
dışı Gerçekten döndürülen `ICorDebugCode` örneklerinin sayısına yönelik bir işaretçi. `celt` bir tane ise bu değer null olabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
