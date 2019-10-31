---
title: ICorDebugCode::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
ms.openlocfilehash: 646c20ca1b78ff0ce513b8a3c9b578c3b1b9a696
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125599"
---
# <a name="icordebugcodegetversionnumber-method"></a>ICorDebugCode::GetVersionNumber Yöntemi

Bu "ICorDebugCode" öğesinin gösterdiği kodun sürümünü tanımlayan tek tabanlı bir sayı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a>Parametreler

 `nVersion`  
 dışı Kodun sürüm numarasına yönelik bir işaretçi.

## <a name="remarks"></a>Açıklamalar

 Kod üzerinde bir Düzenle ve devam et (EnC) işlemi gerçekleştirildiğinde sürüm numarası artırılır.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
