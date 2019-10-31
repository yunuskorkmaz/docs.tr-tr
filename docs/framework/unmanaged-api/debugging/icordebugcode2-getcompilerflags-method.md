---
title: ICorDebugCode2::GetCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: d948fda048e724ad11c59bf7d4776ee2ca6c8d58
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125550"
---
# <a name="icordebugcode2getcompilerflags-method"></a>ICorDebugCode2::GetCompilerFlags Metodu

Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a>Parametreler

`pdwFlags`  
dışı JıT derleyicisinin veya yerel görüntü oluşturucunun davranışını belirten [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
