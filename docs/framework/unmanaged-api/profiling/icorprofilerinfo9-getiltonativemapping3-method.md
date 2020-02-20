---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 22fe5608b0a3f86baf80abb3810a512077954ac3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449757"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi

Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>Parametreler

- `pNativeCodeStartAddress`

  \[, yerel bir işlevin başlangıcına yönelik bir işaretçidir.

- `cMap`

  \[içinde] `map` dizisinin en büyük boyutu.

- `pcMap`

  \[out] kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.

- `map`

  \[out] her biri, uzaklıkları belirten [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıların bir dizisidir. `GetILToNativeMapping3` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.

## <a name="remarks"></a>Açıklamalar

Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir. [ICorProfilerInfo9:: Getnativecodestartaaddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 arabirimi](icorprofilerinfo9-interface.md)
