---
title: 'ICorProfilerInfo10:: ısfrozenobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: b6dabefceba038a129148f7ba36d4ffcfc425c80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790032"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: ısfrozenobject yöntemi

ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>Parametreler

- `objectId`

  \[içinde] incelenecek nesne.

- `pbFrozen`

  \[out] nesnenin salt okunurdur bir kesimde olup olmadığını belirten bir `BOOL`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 arabirimi](icorprofilerinfo10-interface.md)
