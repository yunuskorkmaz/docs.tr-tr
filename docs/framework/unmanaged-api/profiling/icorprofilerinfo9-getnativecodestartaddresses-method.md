---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi'
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
ms.openlocfilehash: 062aebf6d5bed208ea71b215bd9f857b82483673
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759058"
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

`functionId` 'ndaki Yerel kod başlatma adresleri döndürülecek olan işlevin KIMLIĞI.

`reJitId` 'ndaki JıT-yeniden derleme işlevinin kimliği.

`cCodeStartAddresses` 'ndaki Dizinin en büyük boyutu `codeStartAddresses` .

`pcCodeStartAddresses` dışı Kullanılabilir adreslerin sayısı.

`codeStartAddresses` dışı `UINT_PTR`Her birinin, belirtilen işlev için yerel gövde başlangıç adresi olan dizisi.

## <a name="remarks"></a>Açıklamalar

Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 Arabirimi](icorprofilerinfo9-interface.md)
