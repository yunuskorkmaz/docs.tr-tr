---
title: 'ICorProfilerInfo10:: EnumerateObjectReferences'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7fd62e0d3d9173f3b75882131e57126075c0677f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863315"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences yöntemi

Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>Parametreler

- `objectId`

  \[içinde] başvuruların numaralandırılacağı nesne.

- `callback`

  \[içinde] nesnenin başvuruları ile çağrılacak işlev.

- `clientData`

  \[Profiler-`callback` işlevine geçirilecek verileri sağladı.

## <a name="remarks"></a>Açıklamalar

`EnumerateObjectReferences` yöntemi [nesne başvurularına](icorprofilercallback-objectreferences-method.md)benzerdir, ancak başvuruları depolamak için bir diziyi önceden ayırmak yerine, Profil Oluşturucu için isteğe bağlı başvuruları açıklar.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 arabirimi](icorprofilerinfo10-interface.md)
