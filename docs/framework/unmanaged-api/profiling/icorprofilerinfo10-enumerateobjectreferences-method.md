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
ms.openlocfilehash: a276ecfe65ed9752f39ed68a36e8e17a24255508
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558322"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences yöntemi

Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.

## <a name="syntax"></a>Söz dizimi

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

  \[içinde] profil oluşturucu-işleve geçirilecek veriler `callback` .

## <a name="remarks"></a>Açıklamalar

`EnumerateObjectReferences`Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, [ObjectReferences](icorprofilercallback-objectreferences-method.md)'a benzerdir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 Arabirimi](icorprofilerinfo10-interface.md)
