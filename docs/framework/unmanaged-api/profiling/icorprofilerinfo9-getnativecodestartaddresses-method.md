---
title: 'ICorProfilerInfo9:: Getnativecodestartaadresler'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 99706fdc3d60a5e1a7f85400c1184d5acc808e42
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449741"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi

Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] yerel kod başlatma adresleri döndürülecek işlevin KIMLIĞI.

- `reJitId`

  \[içinde] JıT-yeniden derleme işlevinin kimliği.

- `cCodeStartAddresses`

  \[içinde] `codeStartAddresses` dizisinin en büyük boyutu.

- `pcCodeStartAddresses`

  \[out] kullanılabilir adreslerin sayısı.

- `codeStartAddresses`

  \[out] her biri, belirtilen işlev için yerel bir gövde için başlangıç adresi olan bir `UINT_PTR`dizisi.

## <a name="remarks"></a>Açıklamalar

Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 arabirimi](icorprofilerinfo9-interface.md)
