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
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452246"
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

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 arabirimi](icorprofilerinfo10-interface.md)
