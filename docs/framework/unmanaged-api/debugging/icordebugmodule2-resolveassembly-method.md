---
title: ICorDebugModule2::ResolveAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125300"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly Yöntemi

Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>Parametreler

`tkAssemblyRef`\
'ndaki Derlemeye başvuran bir `mdToken` değeri.

`ppAssembly`\
dışı Derlemeyi temsil eden ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi.

## <a name="remarks"></a>Açıklamalar

`ResolveAssembly` çağrıldığında derleme zaten yüklü değilse, CORDBG_E_CANNOT_RESOLVE_ASSEMBLY HRESULT değeri döndürülür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
