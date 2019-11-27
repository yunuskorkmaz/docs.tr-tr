---
title: 'ICorProfilerInfo10:: GetLOHObjectSizeThreshold'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7a38ee4ae74ca5b96dd082e752fc733eb85fca3f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427028"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi

Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a>Parametreler

`pThreshold` \
dışı Bayt cinsinden büyük nesne yığın eşiği.

## <a name="remarks"></a>Açıklamalar

Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır. .NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir `pThreshold`, etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
