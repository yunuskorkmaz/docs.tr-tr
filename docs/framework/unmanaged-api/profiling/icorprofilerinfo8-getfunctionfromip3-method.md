---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868336"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi

Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler. Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a>Parametreler

- `ip`

  \[, Yönetilen koddaki yönerge işaretçisi.

- `pFunctionId`

  \[out] işlev KIMLIĞI.

- `pReJitId`

  \[out] işlevin JıT-yeniden derlenmesi sürümünün kimliği.

## <a name="remarks"></a>Açıklamalar

Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir. Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo8 arabirimi](icorprofilerinfo8-interface.md)
