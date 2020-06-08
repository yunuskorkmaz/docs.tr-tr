---
title: 'ICorProfilerInfo8:: Getdynamicfunctionınfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495326"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi

Dinamik yöntemler hakkında bilgi alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>Parametreler

- `functionId`

  \[' de] bilgi alınacak işlevin KIMLIĞI.

- `moduleId`

  \[' de] işlevin üst sınıfının tanımlandığı modülün bir işaretçisi.

- `ppvSig`

  \[out] işlev için imzaya yönelik bir işaretçi.

- `pbSig`

  \[out] işlev imzası için bayt sayısına yönelik bir işaretçi.

- `cchName`

  \[' de] dizinin en büyük boyutu `wszName` .

- `pcchName`

  \[out] dizideki karakterlerin sayısı `wszName` .

- `wszName`

  \[out] bir dizi varsa `WCHAR` işlevin adıdır.

## <a name="remarks"></a>Açıklamalar

Il saplamaları veya LCG gibi bazı yöntemlerin [IMetaDataImport](../metadata/imetadataimport-interface.md) ve [IMetaDataImport2](../metadata/imetadataimport2-interface.md) API 'leri kullanılarak alınabilecek ilişkili meta verileri yoktur. Bu tür yöntemlere profil oluşturucular ile yönerge işaretçileri aracılığıyla veya [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)dinleyerek erişilebilir.

Bu API, varsa kolay bir ad dahil dinamik yöntemler hakkında bilgi almak için kullanılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo8 Arabirimi](icorprofilerinfo8-interface.md)
