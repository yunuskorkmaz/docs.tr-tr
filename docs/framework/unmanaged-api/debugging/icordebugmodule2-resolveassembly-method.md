---
description: 'Daha fazla bilgi edinin: ICorDebugModule2:: ResolveAssembly Yöntemi'
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
ms.openlocfilehash: fba53b8ff76e4d3deb1876d2a20a7a2edc20bd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722600"
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
'ndaki `mdToken` Derlemeye başvuran bir değer.

`ppAssembly`\
dışı Derlemeyi temsil eden ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi.

## <a name="remarks"></a>Açıklamalar

, Çağrıldığında derleme zaten yüklü değilse `ResolveAssembly` , CORDBG_E_CANNOT_RESOLVE_ASSEMBLY HRESULT değeri döndürülür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
