---
title: 'ICorProfilerInfo8:: ısfunctiondynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861742"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: ısfunctiondynamic yöntemi

Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde, söz konusu işlevi tanımlayan `FunctionID`.

- `isDynamic`

  \[out] işlevin meta veri içermediğini belirten bir değer içeren bir `BOOL` işaretçisi.

## <a name="remarks"></a>Açıklamalar

Bir işlev, meta veri yoksa dinamik olarak değerlendirilir. Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur. Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo8 arabirimi](icorprofilerinfo8-interface.md)
