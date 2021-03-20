---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi'
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
ms.openlocfilehash: b38bd7a4f440edba0a7156176f223ba38c9807cf
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759123"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: Getdynamicfunctionınfo yöntemi

Dinamik yöntemler hakkında bilgi alır.

## <a name="syntax"></a>Sözdizimi

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

`functionId` 'ndaki Bilgi alınacak işlevin KIMLIĞI.

`moduleId` 'ndaki İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.

`ppvSig` dışı İşlev için imzaya yönelik bir işaretçi.

`pbSig` dışı İşlev imzası için bayt sayısına yönelik bir işaretçi.

`cchName` 'ndaki Dizinin en büyük boyutu `wszName` .

`pcchName` dışı Dizideki karakterlerin sayısı `wszName` .

`wszName` dışı Bir dizi, varsa `WCHAR` işlevin adıdır.

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
