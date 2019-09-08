---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Put işlevi, adlandırılmış niteleyiciyi ve değerini yazar.
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
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798265"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put işlevi

Adlandırılmış niteleyiciyi ve değeri yazar. Yeni niteleyici, aynı ada sahip bir önceki değerin üzerine yazar. Niteleyici yoksa, oluşturulur.

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
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`wszName`\
'ndaki Yazılacak niteleyicinin adı.

`pVal`\
'ndaki Yazılacak niteleyiciyi içeren geçerli `VARIANT` bir işaretçisi. Bu parametre `null`olamaz.

`lFlavor`\
'ndaki Bu niteleyici için istenen niteleyici türlerini tanımlayan aşağıdaki sabitlerden biri. Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Niteleyici, türetilmiş bir sınıfta veya örnekte geçersiz kılınabilir. **Bu varsayılan değerdir.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1\. | Niteleyici örneklere yayılır. |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Niteleyici türetilmiş sınıflara yayılır. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | Niteleyici, türetilmiş bir sınıfta veya örnekte geçersiz kılınamaz. |
| `WBEM_FLAVOR_AMENDED` | 0x80 | Niteleyici yereldir. |

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Anahtar olmayan bir özellikte **anahtar** niteleyicisi belirtmeye yönelik geçersiz bir girişim vardı. Anahtarlar bir nesne için sınıf tanımında belirtilir ve örnek temelinde değiştirilemez. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametre geçerli bir niteleyici türü değil. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Sahip olan nesne geçersiz kılmalara izin `QualifierSet_Put` vermediğinden, niteleyicinin yöntemi çağrılamaz. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
