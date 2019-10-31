---
title: Initialize işlevi (yönetilmeyen API Başvurusu)
description: Initialize işlevi WMI başlatması gerçekleştirir.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127385"
---
# <a name="initialize-function"></a>Initialize işlevi

WMI başlatması gerçekleştirir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a>Parametreler

`bAllowIManagementObjectQI`

[in] WMI nesnelerinde QueryInterface çağrılarına izin verildiğini belirtmek için `true`; Aksi takdirde `false`.

## <a name="return-value"></a>Dönüş değeri

İşlev her zaman `S_OK` (0) döndürür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. def

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
