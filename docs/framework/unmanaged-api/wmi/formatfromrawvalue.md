---
title: FormatFromRawValue fonksiyonu (Yönetilmeyen API Başvurusu)
description: FormatFromRawValue işlevi ham performans verilerini belirli bir biçime dönüştürür.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176844"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue işlevi
Biçim dönüştürme zamana dayalıysa, bir ham performans veri değerini belirtilen biçime veya iki ham performans veri değerine dönüştürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a>Parametreler

`dwCounterType`\
[içinde] Sayaç türü. Sayaç türlerinin listesi için [WMI Performans Sayacı Türleri'ne](/windows/desktop/WmiSdk/wmi-performance-counter-types)bakın. `dwCounterType`dışında herhangi bir sayaç `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`türü olabilir ve .

`dwFormat`\
[içinde] Ham performans verilerini dönüştürmek için biçim. Aşağıdaki değerlerden biri olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Hesaplanan değeri çift duyarlıklı kayan nokta değeri olarak döndürün. |
| `PDH_FMT_LARGE` | 0x00000400 | Hesaplanan değeri 64 bit tamsayı olarak döndürün. |
| `PDH_FMT_LONG` | 0x00000100 | Hesaplanan değeri 32 bit tamsayı olarak döndürün. |

Önceki değerlerden biri, aşağıdaki ölçekleme bayraklarından biriyle ORed olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Sayacın ölçekleme faktörlerini uygulamayın. |
| `PDH_FMT_1000` | 0x00002000 | Son değeri 1.000 ile çarpın. |

`pTimeBase`\
[içinde] Biçim dönüştürme için gerekirse zaman tabanına işaretçi. Biçim dönüştürme için zaman temel bilgileri gerekli değilse, bu parametrenin değeri yoksayılır.

`pRawValue1`\
[içinde] Ham performans [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) değerini temsil eden bir yapının işaretçisi.

`pRawValue2`\
[içinde] İkinci ham [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) performans değerini temsil eden bir yapının işaretçisi. İkinci bir ham performans değeri gerekli değilse, `null`bu parametre .

`pFmtValue`\
[çıkış] Biçimlendirilmiş performans [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) değerini alan bir yapının işaretçisi.

## <a name="return-value"></a>Döndürülen değer

Aşağıdaki değerler bu işlevle döndürülür:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | İşlev çağrısı başarılı oldu. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Gerekli bir bağımsız değişken eksik veya yanlış. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Tanıtıcı geçerli bir PDH nesnesi değildir. |

## <a name="remarks"></a>Açıklamalar

Bu [işlev, FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) işlevine bir çağrı yıkıyor.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).

 **Kütüphane:** Perfcounter.dll

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
