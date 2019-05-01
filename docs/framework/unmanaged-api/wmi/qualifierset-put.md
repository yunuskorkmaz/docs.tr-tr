---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: Adlandırılmış niteleyicisi ve değerini QualifierSet_Put işlevi yazar.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e42cf3440bef030f5c7bec71ed1b4b875b79a61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000278"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put işlevi

Değer ve adlandırılmış niteleyicisi yazar. Yeni niteleyici aynı adlı önceki değerin üzerine yazar. Niteleyici mevcut değilse oluşturulur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
[in] Bu parametre kullanılmaz.

`ptr`\
[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.

`wszName`\
[in] Yazılacak niteleyicisi adı.

`pVal`\
[in] Geçerli bir işaretçi `VARIANT` yazılacak niteleyicisi içeriyor. Bu parametre olamaz `null`.

`lFlavor`\
[in] Bu niteleyici için'istenen niteleyici özelliği tanımlayan sabitlerden biri. Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınabilir. **Varsayılan değer budur.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1. | Niteleyici örneklere yayılır. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Türetilmiş sınıflara niteleyici yayılır. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınamaz. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Niteleyici yerelleştirilir. |

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Belirtmek için geçersiz bir girişimde bulunuldu oluştu **anahtar** niteleyici bir özellikte bir anahtar olamaz. Anahtarları belirtilen om c; bir nesne için sınıf tanımı ve örnek başına temelinde değiştirilemez. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametresi geçerli bir niteleyici türü değil. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Çağrı mümkün değil `QualifierSet_Put` edinilen nesneyi izin vermediğinden niteleyici yöntemini geçersiz kılar. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils.idl

**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)