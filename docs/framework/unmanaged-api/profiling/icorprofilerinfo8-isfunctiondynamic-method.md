---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo8:: ısfunctiondynamic yöntemi'
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
ms.openlocfilehash: 8ab942e6919f8029ef0d1c20336917622a1d22ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646536"
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

  \[içinde] `FunctionID` söz konusu işlevi tanımlayan.

- `isDynamic`

  \[out] `BOOL` işlevin bir meta veri içermediğini belirten bir değer içeren bir işaretçisi.

## <a name="remarks"></a>Açıklamalar

Bir işlev, meta veri yoksa dinamik olarak değerlendirilir. Il saplamaları veya LCG yöntemleri gibi bazı yöntemlerin, IMetaDataImport API 'Leri kullanılarak alınabilecek ilişkili meta verileri yoktur. Bu yöntemlere, profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)' i dinleyerek karşılaşılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo8 Arabirimi](icorprofilerinfo8-interface.md)
